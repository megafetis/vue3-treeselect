<script>
  import Input from './Input'
  import Placeholder from './Placeholder'

  export default {
    name: 'vue-treeselect--single-value',
    inject: [ 'instance' ],
    methods: {
      renderSingleValueLabel() {
        const { instance } = this
        const node = instance.selectedNodes[0]

        const customValueLabelRenderer = instance.$slots['value-label']
        return customValueLabelRenderer
          ? customValueLabelRenderer({ node })
          : node.label
      },
    },
    render() {
      const { instance } = this
      const shouldShowValue = instance.hasValue && !instance.trigger.searchQuery

      return (
        <div class="vue-treeselect__value-container">
        
          {[
            shouldShowValue && (
              <div class="vue-treeselect__single-value">
                { this.renderSingleValueLabel() }
              </div>
            ),
            <Placeholder />,
            <Input ref="input" />,
          ]}
        </div>
      )
    },
  }
</script>
