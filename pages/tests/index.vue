<template>
  <section class="container">
    <h1 class="title is-2">疎通確認とかのテスト系</h1>
    <button class="button" @click="hello()">HelloRequest</button>
    <hr>
  </section>
</template>
<script>
import { HelloRequest } from '../../protoc/sample/helloworld_pb'
import { GreeterClient } from '../../protoc/sample/helloworld_grpc_web_pb'
export default {
  methods: {
    hello() {
      const request = new HelloRequest()
      console.log(request) // es-lint-disable-line
      const client = new GreeterClient('http://localhost:9990', {}, {})
      client.sayHello(request, {}, (err, res) => {
        console.log('error', err)
        console.log('response', res)
      })
    },
  },
}
</script>
<style lang="scss" scoped>
</style>
