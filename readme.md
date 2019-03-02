# j-vue-password

The vue password(identifying code) component for H5.

## Github
https://github.com/chuanjing/j-vue-password;
## NPM
https://www.npmjs.com/package/j-vue-password;

## Default style 
 ![image](https://github.com/chuanjing/j-vue-password/blob/master/assets/j-vue-password.gif)
## Custom style
 ![image](https://github.com/chuanjing/j-vue-password/blob/master/assets/custom-password.gif)
## Installation
```
npm i j-vue-password
# or
cnpm i j-vue-password
```

## Example
```
<template>
	<div style="padding: 50px 0;">
    <Password
      default-color="blue"
      active-color="red"
      border-radius="10px"
      :item-style="{ background: '#eee', width: '60px' }"
      :length="6"
      :auto-focus="true"
      :auto-blur="false"
      v-model="passwordVal" 
      @on-finished="onFinished"
      @on-changed="onchanged"/>
      <div style="padding: 50px;">
        <div>
          passwordVal: {{passwordVal}}
        </div>
        <div>
          onchanged: {{changedVal}}
        </div>
        <div>
          onFinished: {{finishedVal}}
        </div>
      </div>
  </div>
</template>

<script>
import Password from "j-vue-password"
export default {
	components: {
		Password: Password
  },
  data() {
    return {
      passwordVal: undefined,
      changedVal: undefined,
      finishedVal: undefined
    }
  },
  methods: {
    onFinished(val) {
      this.finishedVal = val
    },
    onchanged(val) {
      this.changedVal = val
    }
  },
}
</script>
```

## Props
| props-name  | type | desc                                   | default                                           |
| -------------|------- | -------------------------------------- | ------------------------------------------------- |
| length        |Number| the length of the password             | 6                                                 |
| auto-focus    | Boolean | focus when component mounted           | true                                              |
| auto-blur     |Boolean |blur when finished the input           | false                                             |
| v-model       |Number |bind the value like input element      |                                                   |
| default-color |String |the border & circle color when invalid | "#ddd"                                             |
| active-color  | String|the border & circle color when active  |   "#BEA473"                                                |
| border-radius | String|border-radius                          |   "2px"                                                |
| item-style    | Object|the style of input box                 | {width: "50px",height:"50px",	background: "#fff"} |
## Events
| event-name  | desc                                   | default |
| ----------- | -------------------------------------- | ------- |
| on-changed  | emit the value when the value changed  |         |
| on-finished | emit the value when the input finished |         |
## Issue
If you find any issue , feel free post it at https://github.com/chuanjing/j-vue-password/issues.
## License
MIT
## Other
Starred the "j-vue-please", if it can help you. 
