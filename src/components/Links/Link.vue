<script>
export default {
    functional: true,
    props: ['link'],
    render: function (createElement, context) {
      return createElement('a', Object.assign(context.data, context.props.link.data), context.props.link.children)
    }
}
</script>

<style media="screen" scoped>
  a[target="_blank"]:after {
    content: "\29C9";
    text-align: right;
    float:right;
  }
</style>
