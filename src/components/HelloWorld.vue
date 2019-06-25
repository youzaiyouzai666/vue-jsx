<script lang="tsx">
import {
  VNode,
  CreateElement,
  FunctionalComponentOptions,
  RenderContext
} from 'vue'
import { Component, Vue, Prop } from 'vue-property-decorator'

@Component
export default class HelloWorld extends Vue {
  @Prop() msg!: string
  public world: string = 'World222333'

  public render(h: CreateElement): VNode {
    const { world, msg } = this
    const style = {
      fontSize: '64px',
      color: '#3ab981'
    }
    return (
      <h1 style={style}>
        <Child2>{msg}</Child2>
        <Child2>Hello</Child2> <Child2>{world}</Child2>
      </h1>
    )
  }
}

// tslint:disable:max-classes-per-file
@Component
class Child extends Vue {
  public render(h: CreateElement): VNode {
    return <span>{this.$slots.default[0]}</span>
  }
}

// tslint:disable:max-classes-per-file
@Component({
  functional: true
} as FunctionalComponentOptions)
class Child2 extends Vue {
  public render(h: CreateElement, context: RenderContext): VNode {
    return <span>{context.children[0]}</span>
  }
}
</script>

<style>
h1 {
  font-size: 64px;
  color: #3ab981;
}
</style>