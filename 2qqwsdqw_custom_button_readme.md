在odoo的前端页面，我们也许需要在【创建】【导入】等按钮后，增加自定义按钮，这种odoo没有提供的按钮. 代码下载：https://github.com/billhepeng/custom_button.git https://gitee.com/hepeng1/custom_button.git 1：实现目录结构: custom_user_tree.xml：template文件 custom_user_tree.js：JS文件定义 templates.xml：页面加载JS views.xml：视图。

2：custom_user_tree.xml 定义按钮

按钮
 
     
          
            if (window.odoo._modules.indexOf("base_import") >= 0) {
                r.push(context.engine.tools.call(context, 'ImportView.import_button', dict));
            };
         
         
     
 
2：custom_user_tree.js JS 实现 这个文件主要是监听上面定义的按钮，根据触发的事件，操作后台，self.do_action 是触发后台动作 odoo.define('custom_button.user.tree', function (require) { "use strict"; var core = require('web.core'); var ListController = require('web.ListController'); var ListView = require('web.ListView'); var viewRegistry = require('web.view_registry');
var qweb = core.qweb;

var ContactListController = ListController.extend({
    buttons_template: 'CustomListView.buttons',
    /**
     * Extends the renderButtons function of ListView by adding an event listener
     * on the bill upload button.
     *
     * @override
     */
    renderButtons: function () {
        this._super.apply(this, arguments); // Possibly sets this.$buttons
        if (this.$buttons) {
            var self = this;
            this.$buttons.on('click', '.o_list_user_button', function () {
                var state = self.model.get(self.handle, {raw: true});
                var context = state.getContext()
                context['type'] = 'in_invoice'
                self.do_action({
                    type: 'ir.actions.act_window',
                    res_model: 'account.invoice.import.wizard',
                    target: 'new',
                    views: [[false, 'form']],
                    context: context,
                });
                // var state = self.model.get(self.handle, {raw: true});
                // self._rpc({
                //     model: 'crm.team',
                //     method: 'convertteamaddres',
                //     args: [self.res_id]
                // }).then(function (result) {
                //
                // });


            });
        }
    }
});

var ContactListView = ListView.extend({
    config: _.extend({}, ListView.prototype.config, {
        Controller: ContactListController,
    }),
});

viewRegistry.add('custom_button_user_tree', ContactListView);
}); 3: templates.xml 加载JS

  4: 在相个视图中使用按钮
 
     res.users.tree.custombutton.inherit 
     res.users 
     
     
         
             custom_button_user_tree 
         
     
 
5：__manifest__.py 加载相应的视图 # -*- coding: utf-8 -*- { 'name': "custom_button", 'summary': """ 用户自定义Button """, 'description': """ custom button """, 'author': "hepeng1@163.com", 'website': "http://www.heyanze.com/", 'category': 'Uncategorized', 'version': '0.1', 'depends': ['base'], 'data': [ # 'security/ir.model.access.csv', 'views/views.xml', 'views/templates.xml', ], 'demo': [ 'demo/demo.xml', ], 'qweb': [ "static/src/xml/custom_user_tree.xml" ], } 
6：最终实现效果:

 # 良心友情链接

[腾讯QQ群快速检索](http://u.720life.cn/s/8cf73f7c)

[软件免费开发论坛](http://u.720life.cn/s/bbb01dc0)