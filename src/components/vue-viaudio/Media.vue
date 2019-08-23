<script>
  export default {
    functional: true,
    name: 'Media',
    render: function (createElement, context) {
      if ( !['video', 'audio'].includes(context.props.kind.toLowerCase()) ) {
        return createElement()
      }

      if (context.props.srcObject) {
        context.data.domProps = {
          playsInline: context.props.playsInline || true,
          autoplay: context.props.autoplay || true,
        }
      }

      context.data.domProps = {
        ...context.props,
        ...context.data.domProps
      }
      
      context.data.attrs = {
        ...context.data.attrs, 
        ...context.props.attrs
      }

      return createElement(context.props.kind.toLowerCase(), context.data)
    },
    props: {
      kind: {
        type: String,
        required: true
      },
      muted: {
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
        required: false
      }
    },
  }
</script>

<style></style>