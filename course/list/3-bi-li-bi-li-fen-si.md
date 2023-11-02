
# [持续更新 2023/11/2]金山文档自动获取哔哩哔哩粉丝

1. 打开[金山文档](https://www.kdocs.cn/)官网
登录之后点击左上角的【新建】
选择【Office文档】-> 【表格】
<img src="https://slink.ltd/raw.githubusercontent.com/ymh0000123/tu/main/1.png"  />
2. 选择【空白表格】
进入表格界面点击【效率】->【高级开发】->【AirScipt脚本编辑器】
打开【AirScipt脚本编辑器】之后点击【创建脚本】->【文档共享脚本】
<img src="https://slink.ltd/raw.githubusercontent.com/ymh0000123/tu/main/2.png"  />
3. 复制以下代码
```JavaScrip
llet fs;
let smtp_host = Application.Range("G2").Text;
let smtp_port = parseInt(Application.Range("G3").Text);
let smtp_username = Application.Range("G4").Text;
let smtp_password = Application.Range("G5").Text;
let smtp_secure = Application.Range("G6").Text.toLowerCase() === "true";
let smtp_to = Application.Range("G7").Text;
let blibli_uid = parseInt(Application.Range("G8").Text);
let config_message = Application.Range("G9").Text;
let config_message_send = Application.Range("G10").Text;

// 发起GET请求
let url = "https://api.bilibili.com/x/relation/stat?vmid=" + blibli_uid;

let resp = HTTP.get(url);

if (resp.status !== 200) {
  throw new Error("Error! Status is " + resp.status());
}

let data = resp.json(); // 解析JSON响应

if (data.code === 0) {
  let follower = data.data.follower; // 获取follower数据

  let sheet = Application.ActiveSheet;

  // 寻找第一个空的单元格并记录关注者数量
  let row = 1;
  while (sheet.Range('B' + row).Value !== "") {
    row++;
  }
  // 创建一个Date对象
  var currentDate = new Date();

  // 获取当前中国时间
  var options = { timeZone: 'Asia/Shanghai' };
  var chinaTime = currentDate.toLocaleDateString('en-US', options);

  sheet.Range('A' + row).Value = chinaTime;
  sheet.Range('B' + row).Value = follower;
  fs = follower;
  console.log("粉丝数量：" + fs)
  // 计算A列倒数第一和倒数第二个单元格的差
  let lastRow = row;
  if (lastRow >= 2) {
    let lastFollower = sheet.Range('B' + (lastRow - 1)).Value;
    let diff = fs - lastFollower;
    zj = diff
    if (config_message_send == "是") {
      if (diff == 0) {
        console.log("粉丝不变")
        if (config_message == "是") {
          smtp_message()
        }
      } else {
        console.log("粉丝增加" + diff);
        smtp_message()
      }
    } else {
      console.log("消息发送已经关闭")
    }
  }
} else {
  console.error("API response error: " + data.message);
}

function smtp_message() {
  // 发送邮件通知
  console.log("发送邮件通知")
  let mailer = SMTP.login({
    host: smtp_host,
    port: smtp_port,
    username: smtp_username,
    password: smtp_password,
    secure: smtp_secure,
  });

  mailer.send({
    from: smtp_username,
    to: smtp_to,
    subject: "粉丝数通知",
    html: `
      <div style="background-color: #f0f0f0; padding: 20px;">
        <div style="background-color: #ffffff; padding: 20px; border: 1px solid #ddd; border-radius: 5px;">
          <img border="0" src="https://space.bilibili.com/favicon.ico" width="64" height="64">
          <h4 style="color: #333; font-size: 18px;">哔哩哔哩粉丝数量通知</h4>
          <p style="color: #555; font-size: 16px; margin: 0;">uid: <strong>${blibli_uid}</strong></p>
          <p style="color: #555; font-size: 16px; margin: 0;">当前粉丝数量: <strong>${fs}</strong></p>
          <p style="color: #555; font-size: 16px; margin: 0;">粉丝增加: <strong>${zj}</strong></p>
          
          <p style="text-align: center;">
            <a href="https://space.bilibili.com/${blibli_uid}" style="color: #888; text-decoration: none; border: none; font-style: normal;">查看主页</a> | <a href="https://ymh0000123.github.io/dochub/course/list/3-bi-li-bi-li-fen-si.html" style="color: #888; text-decoration: none; border: none; font-style: normal;">关于脚本-脚本作者没用的小废鼠</a>
          </p>
        </div>
      </div>
    `,
  });
  console.log("发送完毕")
}
```
5. 再按照[模板](https://kdocs.cn/l/cshyjZHnMGFo)填入信息

如果你有定时获取的需求可以在【效率】->【高级开发】->【定时任务】里设置