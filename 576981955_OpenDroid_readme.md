#OpenDroid
一、opendroid的介绍：  
opendroid， android上的一个开源orm框架，可以轻松实现将数据库中的数据映射到java bean中、将java bean持久化到sqlite中。  
opendroid也提供了强大的数据库升级方案，只需修改一个参数即可实现数据库升级，opendroid会自动将旧数据更新到新表中，免除数据库升级数据丢失的烦恼。  

opendroid使用简单，语法简洁，预计10分钟即可完全掌握opendroid的使用。  
以下是opendroid的使用方法，项目中也提供了samples供参考。  

二、opendroid的上手：  
1、将library目录中的opendroid.jar文件copy到你项目的libs目录。 
2、在项目中新建需要映射的java bean文件，并让该类继承自OpenDroid类。 

public class Student extends OpenDroid {

    private String stuName;
	private int stuAge;
	private String stuAddr;

	public String getStuAddr() {
		return stuAddr;
	}

	public void setStuAddr(String stuAddr) {
		this.stuAddr = stuAddr;
	}

	public String getStuName() {
		return stuName;
	}

	public void setStuName(String stuName) {
		this.stuName = stuName;
	}

	public int getStuAge() {
		return stuAge;
	}

	public void setStuAge(int stuAge) {
		this.stuAge = stuAge;
	}
    
}

 
3、在asserts目录中新建open_droid.xml文件 
  
\  
   \   
    \  
	\  
\  

name 指定了数据库的名称， version指定了数据库的版本， mapping指定了需要映射的javabean 

4、配置完成后，开始使用： 

        /**
    	 * step 1 : 插入一条数据， 查询一条数据
		 */
		Student stu = new Student();
		stu.setStuName("亓斌");
		stu.setStuAge(18);
		stu.save();
		
		Student result = OpenDroid.query.find(Student.class, 1);
		System.out.println(result.getStuName());
        
        /**
    	 * step 2 : 查询所有记录
		 */
		for(int i=0;i  result = OpenDroid.query.find(Student.class);
		for(Student res : result) {
			System.out.println(res.getStuName());
		}
        
        /**
    	 * step 3 : 查询多条记录
		 */
		List  result = OpenDroid.query.find(Student.class, 1, 5, 10);
		for(Student res : result) {
			System.out.println(res.getId() + " : " + res.getStuName());
		}
        
        /**
    	 * step 4 : 条件查询
		 */
		List  result = OpenDroid.query.columns("stuName", "stuAge")
				.where("_id>?", "5").order("_id DESC").limit(3)
				.find(Student.class);
		for(Student res : result) {
			System.out.println(res.getStuName() + " : " + res.getStuAge());
		}
        
        
        /**
    	 * step 5 : 更新数据
		 */
		Student stu = new Student();
		stu.setStuName("loader");
		stu.setStuName("loader");
		stu.update(4);
		stu.update("_id>?", "4");
		
		List  result = OpenDroid.query.find(Student.class);
		for(Student res : result) {
			System.out.println(res.getStuName());
		}
        
        /**
    	 * step 6 : 使用ContentValues更新
		 */
		ContentValues cv = new ContentValues();
		cv.put("stuName", "opendroid");
		OpenDroid.update(Student.class, cv, "_id=?", "8");
		
		Student result = OpenDroid.query.find(Student.class, 8);
		System.out.println(result.getStuName());
        
        /**
    	 * step 7 : 特定删除
		 */
		int length = OpenDroid.delete(Student.class, 1, 2, 3);
		System.out.println(length);
        
        /**
    	 * step 8 : 使用条件删除
		 */
		int length = OpenDroid.delete(Student.class, "_id>?", "5");
		System.out.println(length);

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)