### j-vue-password

#### The props & events

##### Props
| props-name | desc                              | default |
| ---------- | --------------------------------- | ------- |
| length     | the length of the password        | 6       |
| auto-focus | focus when component mounted      | true    |
| auto-blur  | blur when finished the input      | false   |
| v-model    | bind the value like input element |         |
##### Events
| event-name | desc | default |
| ---------- | ---- | ------- ||
| on-changed  | emit the value when the value changed  |         |
| on-finished | emit the value when the input finished |

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
	<div>
    <Password
      :length="6"
      :auto-focus="true"
      :auto-blur="false"
      v-model="passwordVal"
      @on-finished="onFinished"
      @on-changed="onchanged"/>
	</div>
</template>

<script>
	import JVuePassword from "j-vue-password"
	export default {
		components: {
			Password: JVuePassword
    },
    data() {
      return {
        passwordVal: undefined
      }
    },
    methods: {
      onFinished(val) {
        console.log('onFinished', val)
      },
      onchanged(val) {
        console.log('onchanged', val)
      }
    },
	}
</script>

```


#### Issue

If you find any issue , feel free post it at https://github.com/chuanjing/j-vue-password/issues.