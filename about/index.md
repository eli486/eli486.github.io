---
title: about
date: 2018-12-12 22:14:36
keywords: 关于
description: 
comments: false
photos: https://cdn.jsdelivr.net/gh/honjun/cdn@1.4/img/banner/about.jpg
---
{% raw %}
<div class="moe-mashiro" style="text-align:center; font-size: 50px; margin-bottom: 20px;">[AlavonのEli]</div>
<div id="hello-mashiro" class="popcontainer" style="min-height: 300px; padding: 2px 6px 4px; background-color: rgba(242, 242, 242, 0.5); border-radius: 10px;">
  <center>
  <p>
  </p>
  <h4>
  与&nbsp;<ruby>
  Eli&nbsp;<rp>
  
  </ruby>
  对话中...</h4>
  <p>
  </p>
  </center>
  <bot-ui></botui>
</div>
<script src="https://cdn.jsdelivr.net/vue/latest/vue.min.js"></script>
<script src="https://unpkg.com/botui/build/botui.min.js"></script>
<script>
function bot_ui_ini() {
    var botui = new BotUI("hello-mashiro");
    botui.message.add({
        delay: 800,
        content: "Selamat pagi👋"
    }).then(function () {
        botui.action.button({
            delay: 900,
            action: [{
                        text: "哦哈呦！ 😃",
                        value: "sure"
                    }, {
                        text: "? 🙄",
                        value: "skip"
                    }]
        }).then(function (a) {
                    "sure" == a.value && sure();
                    "skip" == a.value && end()
                })
    });
    var sure = function () {
            botui.message.add({
                delay: 600,
                content: "😘"
            }).then(function () {
                secondpart()
            })
        },
        end = function () {
            botui.message.add({
                delay: 600,
                content: "![...](https://view.moezx.cc/images/2018/05/06/a1c4cd0452528b572af37952489372b6.md.jpg)"
            })
        },
        secondpart = function () {
            botui.message.add({
                delay: 1500,
                content: "俺毕业于上海立信会计金融学院"
            }).then(function () {
                botui.message.add({
                    delay: 1500,
                    content: "所学专业是数学与应用数学(金融方向)"
                }).then(function () {
                    botui.message.add({
                        delay: 1200,
                        content: "数学系的我只是咸鱼一条，baga一个"
                    }).then(function () {
                        botui.message.add({
                            delay: 1500,
                            content: "考研fail，loser一枚"
                        }).then(function () {
                            botui.message.add({
                                delay: 1500,
                                content: "辗转反侧,投身java"
                            }).then(function () {
                                botui.message.add({
                                    delay: 1800,
                                    content: "我入单身狗之列了!"
                                }).then(function () {
                                    botui.action.button({
                                        delay: 1100,
                                        action: [{
                                            text: "为什么叫Eli呢？ 🤔",
                                            value: "why-mashiro"
                                        }]
                                    }).then(function (a) {
                                        thirdpart()
                                    })
                                })
                            })
                        })
                    })
                })
            })
        },
        thirdpart = function () {
            botui.message.add({
                delay: 1E3,
                content: "外语课上百度搜的name,中文含义:至高无上的 😀"
            }).then(function () {
                botui.action.button({
                    delay: 1500,
                    action: [{
                        text: "为什么是Alavon呢？ 🤔",
                        value: "why-cat"
                    }]
                }).then(function (a) {
                    fourthpart()
                })
            })
        },
        fourthpart = function () {
            botui.message.add({
                delay: 1E3,
                content: "Because  Saber "
            }).then(function () {
                botui.message.add({
                    delay: 1100,
                    content: "I want to be in Alavon and guard my King Arthur"
                })
            })
        }
        
}
bot_ui_ini()
</script>
{% endraw %}