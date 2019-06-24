<script>
// demo.jsx
const ButtonCounter = {
  // inheritAttrs: false,
  name: 'button-counter',
  props: ['count'],
  methods: {
    onClick() {
      console.log('onClick:', this.propsCount)
      this.$emit('change', this.count + 1)
    }
  },
  render(h) {
    return (
      <button onClick={this.onClick}>You clicked me {this.count} times.</button>
    )
  }
}

export default {
  name: 'ButtonCounterContainer',
  data() {
    return {
      count: 0
    }
  },
  methods: {
    onChange(val) {
      this.count = val
    },
    onChange1(val) {
      // this.count = val
      console.log('onChange1', val)
    }
  },
  render(h) {
    const { count, onChange, onChange1 } = this
    const btnProps = {
      props: {
        count
      },
      on: {
        change: onChange
      },
      attrs: {
        type: 'button'
      },

      style: { marginTop: '10px' }
    }

    return (
      <div>
        <ButtonCounter
          style={{ marginTop: '10px' }}
          type='button'
          count={count}
          onChange={onChange1}
        />
        <br />
        <ButtonCounter {...btnProps} />
        <br />
        <ButtonCounter
          style={{ marginTop: '10px' }}
          count={count}
          type='button'
          domPropsInnerHTML={`hello ${this.count}.`}
          onChange={onChange1}
        />
      </div>
    )
  }
}
</script>
<style>
</style>
