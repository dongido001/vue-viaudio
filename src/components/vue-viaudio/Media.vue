<script>
  export default {
    functional: true,
    name: 'Media',
    render: function (createElement, context) {
      if (!['video', 'audio'].includes(context.props.kind) ) {
        return createElement()
      }
      
      const domProps = {}
 
      if (context.props.isMuted) {
        domProps.muted = context.props.isMuted
      }

      if (context.props.src) {
        domProps.src = context.props.src
      }

      if (context.props.srcObject) {
        domProps.srcObject = srcObject
      }

      if (context.props.ref) {
        context.data.ref = context.props.ref
      }
      
      if (context.props.attrs) {
        context.data.attrs = {
          ...context.data.attrs, 
          ...context.props.attrs
        }
      }

      context.data.domProps = domProps

      return createElement(context.props.kind, context.data)
    },
    props: {
      kind: {
        type: String,
        required: true
      },
      className: {
        type: Object | String | Array
      },
      styles: {
        type: Object | String | Array
      },
      ref: {
        type: String
      },
      isMuted: {
        type: Boolean
      },
      poster: {
        type: String
      },
      src: {
        type: String | Array
      }
    },
  }
</script>

<style></style>