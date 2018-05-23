#####  本项目是模拟链家微信小程序贝壳新房
######  实现了房屋筛选，以及用微信小程序渲染页面
######  渲染数据时用wx.request（）请求接口http://47.93.220.17/Home/Bk/xinfang
####  部分代码实现：
getData: function () {

    const that = this;
    wx.request({
      url: 'http://47.93.220.17/Home/Bk/xinfang',
      header: {
        'content-type': 'application/json' // 默认值
      },
      method: "get",
      dataType: "json",
      success: function (res) {
        that.setData({
          main: res.data

        });
        console.log(that.data.main)
        console.log(res.data.data.typs_conditions)


      }
    })
 
  },
###  房屋筛选
###### 房屋筛选是用wx.request（）请求接口http://47.93.220.17/Home/Bk/getListsByType',
###### 传递参数type_id
###### 主要代码实现：
  clicktype: function (e) {
    const nowId = e.currentTarget.id;
    console.log(nowId)

    const that = this
    wx.request({
      url: 'http://47.93.220.17/Home/Bk/getListsByType',
      method: "get",
      dataType: "json",
      data: {
        type_id: nowId
      },
      success: function (res) {
        that.setData({
          house: res.data
        })
      }
    })
