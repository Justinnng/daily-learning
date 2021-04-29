function jsonp (url) {
  /*声明一个唯一的回调函数并挂载到全局上
   *创建一个script标签地址 指向 请求服务器 将回调函数名作参数带到服务器
   *服务器拿到回调名称 并返回前端 该回调的调用 把返回结果当作参数传入
   */
  let script = document.createElement('script')
  let uniqueName = `jsonpCallback${new Date().getTime()}`
  script.src = `url${url.indexOf('?') > -1 ? '&': '?'}callback=${uniqueName}`
  document.body.appendChild(script)

  window[uniqueName] = (res) => {
    cb && cb(res)
    document.body.removeChild(script)
    delete window[uniqueName]
  }
}
