<template>
    <Page>
        <ActionBar title="WebView YouTube!"/>
        <GridLayout @loaded="setupWebviewInterface">
            <WebView ref="webView"/>
        </GridLayout>
    </Page>
</template>

<script>
  import {WebViewInterface} from 'nativescript-webview-interface'

  export default {
    methods: {
      setupWebviewInterface() {
        console.log('setting up WW interface')
        this.oWebViewInterface = new WebViewInterface(this.$refs.webView.nativeView, '~/www/index.html')

        this.oWebViewInterface.on('playerStateChanged', (data) => {
          console.log(`playerStateChanged`)
          console.log(data)
        })
      }
    }
  }
</script>

<style scoped>
    ActionBar {
        background-color: #53ba82;
        color: #ffffff;
    }

    .message {
        vertical-align: center;
        text-align: center;
        font-size: 20;
        color: #333333;
    }
</style>
