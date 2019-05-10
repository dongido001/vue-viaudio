<script>
  export default {
    functional: true,
    name: 'Media',
    render: function (createElement, context) {
      if ( !['video', 'audio'].includes(context.props.kind.toLowerCase()) ) {
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
        domProps.srcObject = context.props.srcObject
      }

      if (context.props.ref) {
        context.data.ref = context.props.ref
      }
      
      context.data.attrs = {
        ...context.data.attrs, 
        ...context.props.attrs
      }

      context.data.domProps = domProps

      return createElement(context.props.kind.toLowerCase(), context.data)
    },
    props: {
      kind: {
        type: String,
        required: true
      },
      className: {
        type: Object | String | Array,
        required: false
      },
      styles: {
        type: Object | String | Array,
        required: false
      },
      ref: {
        type: String,
        required: false
      },
      isMuted: {
        type: Boolean,
        required: false
      },
      poster: {
        type: String,
        required: false
      },
      src: {
        type: String | Array,
        required: false
      },
      srcObject: {
        type: Object,
        required: false
      }
    },
  }
</script>

<style></style>