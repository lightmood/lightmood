# SwipeOut-Left
![SwipeOut-Left](https://www.dropbox.com/s/7com4d32zct44nc/Vue2Editor-Centered.png?raw=1)

# Install

```bash
$ npm install --save vue2-editor
```

# Usage

```javascript
import { swipeoutLeft, swipeoutItem, swipeoutButton } from "swipeoutLeft";
```

## Props(swipeout-item)

| Name                  | Type    | Default                                              | Description                                  |
| --------------------- | ------- | ---------------------------------------------------- | ---------------------------------------------|
| type                  | String  | 1                                                    | 操作按钮滑动类型                             |
| index                 | String  | -                                                    | 序号                                         |

## Props(swipeout-button)

| Name                  | Type    | Default                                              | Description                                  |
| --------------------- | ------- | ---------------------------------------------------- | ---------------------------------------------|
| text                  | String  | -                                                    | 操作按钮显示文字                             |
| width                 | Number  | 80                                                   | 操作按钮宽度                                 |
| type                  | String  | -                                                    | 操作按钮类型`warn`                           |
| backgroundColor       | String  | -                                                    | 操作按钮背景颜色                             |
| visible               | Boolean | true                                                 | 操作按钮是否可见                             |

# Demo



# Demo Code

```html
<template>
  <div>
    <swipeout-left>
      <swipeout-item v-for="(item,index) in data" :key="index" :index="index" :type="item.type">
        <div slot="right-menu">
          <swipeout-button @click.native="onButtonClick('read', index)" :visible="item.visible!=null?item.visible[0]:true" :width="120" background-color="#c8c8cd">{{item.newItem?"标为已读":"标为未读"}}</swipeout-button>
          <swipeout-button @click.native="onButtonClick('delete', index)" type="warn">删除</swipeout-button>
        </div>
        <div slot="content" class="weui-cell" @click="onButtonClick('content', index)">
          <div class="weui-cell__hd" style="position: relative;margin-right: 10px;">
              <img src="../assets/logo.png" style="width: 50px;display: block">
              <span v-show="item.newItem" class="weui-badge" style="position: absolute;top: -.4em;right: -.4em;">8</span>
          </div>
          <div class="weui-cell__bd">
              <p>{{'Type' + item.type}}</p>
              <p style="font-size: 13px;color: #888888;">{{item.content}}</p>
          </div>
        </div>
      </swipeout-item>
    </swipeout-left>
  </div>
</template>
<script>
import swipeoutLeft from '../components/swipeout-left'
import swipeoutItem from '../components/swipeout-item'
import swipeoutButton from '../components/swipeout-button'
export default {
  name: 'Message',
  components: {
    swipeoutLeft,
    swipeoutItem,
    swipeoutButton
  },
  data () {
    return {
      data: [
        {
          type: '1',
          content: '',
          newItem: false
        },
        {
          type: '1',
          content: 'hide read button',
          newItem: false,
          visible: [false, true]
        },
        {
          type: '2',
          content: '',
          newItem: false
        },
        {
          type: '3',
          content: '',
          newItem: false
        }
      ]
    }
  },
  methods: {
    onButtonClick (type, index) {
      if(type == 'read'){
        this.data[index].newItem = !this.data[index].newItem
      }
      console.log(type, index)
    }
  }
}
</script>
```

# Inspired By

[Vux](https://github.com/airyland/vux)
[WeUI](https://github.com/Tencent/weui)

# License

MIT
