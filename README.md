
# TodoList #
---
> 一个简单的**vue + nodejs**项目，前端由vue实现，后端由**nodejs(express)**，数据库采用**mongodb**。 
---
**前端**：vue
**后端**：Nodejs
**数据库**： mongodb
---
- github: [https://github.com/xiechengbo/netease_todos](https://github.com/xiechengbo/netease_todos)
- 在线效果展示: [http://www.chengbo.xyz](http://www.chengbo.xyz)

## 前端 ##

 1. 使用vue-cli脚手架， vue+axio
 2. 实现的功能

    (1) 单条添加todo
    
    (2) 单条删除todo
    
    (3) 双击编辑todo
    
    (4) 单条todo已完成相应样式状态改变
    
    (5) 全部todo是已完成相应样式状态改变
    
    (6) 清除全部已完成todos
    
    (7) 待办todos数量显示
    
    (8) 所有todos，已完成todos，未完成todos筛选

  

 3. 接口展示

```
    import axios from 'axios'
    
    const baseUrl =
    process.env.NODE_ENV === "development" ?
    "https://nei.netease.com/api/apimock/f3e5d93d5eaceda5a624378374ad5cd7"
    : "http://148.70.150.147:8080"
    
    export const getAllTask = params => { return axios.get(`${baseUrl}/api/all`, {params: params}) }
    export const addTask = params => { return axios.post(`${baseUrl}/api/add`, params).then(res => res.data) }
    export const deleteTask = params => { return axios.post(`${baseUrl}/api/deletes`, params).then(res => res.data) }
    export const updateTask = params => { return axios.post(`${baseUrl}/api/update`, params).then(res => res.data) }
    export const updateManyTask = params => { return axios.post(`${baseUrl}/api/updateMany`, params).then(res => res.data) }
    export const deleteCompletedTask = params => { return axios.post(`${baseUrl}/api/deletemany`, params) }
```
---

## 后端 ##
---
1.后台由`express + mongoodb`构建。

2.路由

   ```javascript
        module.exports = function(app) {
            app.get('/api/all', TodoController.getAll);
            app.post('/api/add', TodoController.newTodo);
            app.post('/api/deletes', TodoController.deleteOne);
            app.post('/api/deletemany', TodoController.deleteAllCompleted);
            app.post('/api/update', TodoController.updateOne);
            app.post('/api/updateMany', TodoController.updateMany);
                ....
   ```
## 项目启动
```bash
$ npm install
// or
$ yarn install
```
## 开发环境

```bash
$ npm run dev
```

