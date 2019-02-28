<template>
	<div class="j-password" @click="onTapWrap">
		<ul class="input-list">
			<li
				:class="{ active: i <= strVal.length }"
				:id="i"
				v-for="i in length"
				class="input-box"
				:style="[itemStyle, { borderColor: getItemColor(i <= strVal.length)}, getBorderRadius(i)]"
			>
				<i
					class="input-box_active"
					:style="{background: getItemColor(i <= strVal.length)}"
					v-show="(i <= strVal.length)"
				></i>
			</li>
			<li class="input-core-wrap">
				<input
					v-model="val"
					ref="inputCore"
					:autoFocus="autoFocus"
					class="input-core"
					:maxlength="length"
					type="tel"
					pattern="[0-9]"
				/>
			</li>
		</ul>
	</div>
</template>

<script>
	export default {
		name: "j-vue-password",
		props: {
			value: {
				type: [String, Number]
			},
			length: {
				type: Number,
				default: 6
			},
			"item-style": {
				type: Object,
				default: function() {
					return {
						width: "50px",
						height: "50px",
						background: "#fff"
					}
				}
			},
			"auto-focus": {
				type: Boolean,
				default: function() {
					return false
				}
			},
			"auto-blur": {
				type: Boolean,
				default: function() {
					return false
				}
			},
			"default-color": {
				type: String,
				default: function() {
					return "#ddd"
				}
			},
			"active-color": {
				type: String,
				default: function() {
					return "#BEA473"
				}
			},
			"border-radius": {
				type: String,
				default: function() {
					return "2px"
				}
			}
		},
		data() {
			return {
				val: null,
				strVal: ""
			}
		},
		created() {
			let self = this
			let { value, autoFocus } = self
			if (!value) {
				self.strVal = ""
				self.val = ""
			} else {
				self.strVal = self.value + ""
				self.val = self.value + ""
			}
		},
		mounted() {
			this.autoFocus && this.$refs["inputCore"].focus()
		},
		computed: {},
		methods: {
			getBorderRadius: function(index = 0) {
				let { borderRadius, length } = this
				let borderRadiusStyle = {}
				if (index === 1) {
					borderRadiusStyle = {
						borderBottomLeftRadius: borderRadius,
						borderTopLeftRadius: borderRadius
					}
				}
				if (index === length) {
					borderRadiusStyle = {
						borderBottomRightRadius: borderRadius,
						borderTopRightRadius: borderRadius
					}
				}
				return borderRadiusStyle
			},
			getItemColor: function(isActive = false) {
				let { defaultColor, activeColor } = this
				let styles = {}
				return isActive ? activeColor : defaultColor
			},
			reset() {
				this.val = ""
				this.strVal = ""
			},
			onTapWrap() {
				this.$refs["inputCore"].focus()
			}
		},
		watch: {
			val(val, oldVal) {
				if ((val + "").length > this.length) {
					return
				}
				this.$emit("input", val)
				this.$emit("on-changed", val)
				if ((val + "").length === this.length) {
					this.autoBlur && this.$refs["inputCore"].blur()
					this.$emit("on-finished", val)
				}
			},
			value: function(val, oldVal) {
				let self = this
				self.$nextTick(function() {
					self.strVal = val + ""
					self.val = val
				})
			}
		}
	}
</script>

<style lang="css">
	.j-password {
		text-align: center;
	}

	.j-password * {
		transition: .28s;
	}

	.j-password .input-list {
		position: relative;
		box-sizing: content-box;
	}

	.j-password .input-box {
		position: relative;
		display: inline-block;
		background: #fff;
		width: 50px;
		height: 50px;
		border-right: 1px solid #ddd;
		border-top: 1px solid #ddd;
		border-bottom: 1px solid #ddd;
	}

	.j-password .input-box:first-child {
		border-left: 0.01rem solid #ddd;
		border-bottom-left-radius: 2px;
		border-top-left-radius: 2px;
	}
	.j-password .input-box:nth-last-child(2){
		border-bottom-right-radius: 2px;
		border-top-right-radius: 2px;
	}

	.j-password .input-box.active {
		border-right: 1px solid #BEA473 ;
		border-top: 1px solid #BEA473 ;
		border-bottom: 1px solid #BEA473 ;
	}

	.j-password .input-box_active {
		display: block;
		position: absolute;
		width: 15px;
		height: 15px;
		z-index: 10;
		content: ' ';
		background: #BEA473;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		border-radius: 100%;
	}

	.j-password .input-box:first-child.active {
		border-left: 1px solid #BEA473;
	}

	.j-password .input-core-wrap {
		display: block;
		position: absolute;
		width: 100%;
		height: 100%;
		left: -300%;
		top: 0;
		z-index: 99;
	}

	.j-password .input-core {
		display: block;
		width: 100%;
		height: 100%;
		background: transparent;
		color: transparent;
		border: none;
		outline: none;
		caret-color: transparent;
		opacity: 0;
	}
</style>
