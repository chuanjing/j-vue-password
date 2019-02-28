### j-vue-password

The j-vue-password is basic on vue2 .

#### The github link is https://github.com/chuanjing/j-vue-password;
#### The npmjs link is https://www.npmjs.com/package/j-vue-password;

### default style 
 ![image](https://github.com/chuanjing/j-vue-password/blob/master/assets/j-vue-password.gif)
### custom style
 ![image](https://github.com/chuanjing/j-vue-password/blob/master/assets/custom-password.gif)
#### How to use ?

##### Step 1: install the package from npmjs
```
npm/cnpm i j-vue-password
```

##### Step 2: import the package into your component
```
import Password from "j-vue-password"
```
##### Step 3: Below is the demo that how to use j-vue-password.
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
#### The props & events

##### Props
| props-name    | desc                                   | default                                           |
| ------------- | -------------------------------------- | ------------------------------------------------- |
| length        | the length of the password             | 6                                                 |
| auto-focus    | focus when component mounted           | true                                              |
| auto-blur     | blur when finished the input           | false                                             |
| v-model       | bind the value like input element      |                                                   |
| default-color | the border & circle color when invalid | "#ddd"                                             |
| active-color  | the border & circle color when active  |   "#BEA473"                                                |
| border-radius | border-radius                          |   "2px"                                                |
| item-style    | the style of input box                 | {width: "50px",height:"50px",	background: "#fff"} |
|               |
##### Events
| event-name  | desc                                   | default |
| ----------- | -------------------------------------- | ------- |
| on-changed  | emit the value when the value changed  |         |
| on-finished | emit the value when the input finished |         |

#### Issue

If you find any issue , feel free post it at https://github.com/chuanjing/j-vue-password/issues.
