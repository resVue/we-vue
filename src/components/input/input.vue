<template>
  <div class="weui-cell">
    <div class="weui-cell__hd">
      <label class="weui-label" v-html="label" v-if="label" :style="{ width: labelWidth + 'px' }"></label>
    </div>
    <div class="weui-cell__bd">
      <input
        class="weui-input"
        rel="input"
        :type="type"
        :number="type === 'number'"
        @focus="active = true"
        :placeholder="placeholder"
        :value="currentValue"
        :readonly="readonly"
        @change="$emit('change', currentValue)"
        @input="handleInput">
    </div>
    <div class="weui-cell__ft">
      <slot name="ft"></slot>
    </div>
  </div>
</template>

<script type="text/babel">
export default {
  name: 'wv-input',

  props: {
    type: {
      type: String,
      default: 'text'
    },
    label: String,
    labelWidth: {
      type: Number,
      default: 105
    },
    placeholder: String,
    value: String,
    readonly: Boolean,
    disabled: Boolean,
    state: {
      type: String,
      default: 'default'
    }
  },

  data () {
    return {
      active: false,
      currentValue: this.value
    }
  },

  methods: {
    doCloseActive () {
      this.active = false
    },

    handleInput (event) {
      this.currentValue = event.target.value
    },

    handleClear () {
      if (this.disabled || this.readonly) return
      this.currentValue = ''
    }
  },

  watch: {
    currentValue (val) {
      this.$emit('input', val)
    },

    value (val) {
      this.currentValue = val
    }
  }
}
</script>
