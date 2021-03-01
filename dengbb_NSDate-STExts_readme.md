 日期常用方法 
 日期常用方法，字符串和日期的便捷转换，还可以像日历一样获取日期的年、月、日、时、分、秒等。扩展了日期加减年、月、日、时、分、秒获取另一个日期。
 
 字符串和日期相互转换 
  NSDate *today = [NSDate date];
// 生成日期时间字符串,默认格式为yyyy-MM-dd HH:mm:ss
NSString *dateTimeStr = [today string]; 
// 生成日期字符串,默认格式yyyy-MM-dd
NSString *dateStr = [today dateString];
// 生成时间字符串，默认格式HH:mm:ss
NSString *timeStr = [today timeString];

// 根据日期时间字符串生成日期对象
NSDate *dateTimeDate = [NSDate dateWithString:@"2013-06-30 07:30:04"];
// 根据日期字符串生成日期对象
NSDate *dateDate = [NSDate dateWithDateString:@"2013-06-30"];
// 根据时间字符串生成日期对象
NSDate *timeDate = [NSDate dateWithTimeString:@"07:30:04"];
  
 获取日期的年、月、日、时、分、秒 
  // 年
NSInteger year = today.year;
// 月
NSInteger month = today.month;
// 日
NSInteger day = today.day;
// 时
NSInteger hour = today.hour;
// 分
NSInteger min = today.minute;
// 秒
NSInteger sec = today.second;
  

 根据一个日期生成另一个日期 
  // 明天
NSDate *tomorrow = [today dateByAddingDays:1];
// 昨天
NSDate *yestday = [today dateByAddingDays:-1];
// 上个月的日期
NSDate *preMonthDate = [[NSDate date] dateByAddingMonths:-1];
// 下一年的日期
NSDate *nextYearDate = [[NSDate date] dateByAddingYears:1];
  

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)