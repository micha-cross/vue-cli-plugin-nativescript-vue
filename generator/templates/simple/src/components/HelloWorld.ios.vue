<template>
  <GridLayout rows="auto, auto">
    <Label class="message" :text="msg" row="0" horizontalAlignment="center"/>
    <!-- copy-webpack-plugin copies asset from src/assets to project output/build directory /assets -->
    <Image src="~/components/icon.png" row="1" class="m-40"/>
  </GridLayout>
</template>
<%_ if (!usingTS) { _%>
<%# -------------------- Is Not Using TypeScript  -------------------- -%>
<script>
  export default {
    name: 'HelloWorld',
    props: {
      msg: String
    }
  };
</script>
<%_ } else { _%>
<%# -------------------- Is Using TypeScript  -------------------- -%>
<script lang="ts">
  import { Component, Vue, Prop } from 'vue-property-decorator';

  @Component({
    name: 'HelloWorld',
  })
  export default class HelloWorld extends Vue {
    @Prop(String) private msg!: string;
  }

</script>
<%_ } _%>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<%_ if (rootOptions.cssPreprocessor) { _%>
<%_   if (rootOptions.cssPreprocessor == 'sass' || rootOptions.cssPreprocessor == 'scss'  || rootOptions.cssPreprocessor == 'dart-sass' ) { _%>
<%#   -------------------- IS Using sass, scss OR dart-sass -------------------- -%>
<style scoped lang="scss">
  .message {
    color: #42b983;
  }

  Image {
    height: 20%;
    width: 20%;
    margin-top: 20px;
  }
</style>
<%_   } else if (rootOptions.cssPreprocessor == 'stylus') { _%>
<%#   -------------------- IS Using stylus -------------------- -%>
<style scoped lang="stylus">
  .message
    color #42b983

  Image
    height 20%
    width 20%
    margin-top 20px
</style>
<%_   } else if (rootOptions.cssPreprocessor == 'less') { _%>
<%#   -------------------- IS Using Less -------------------- -%>
<style scoped lang="less">
  .message {
    color: #42b983;
  }

  Image {
    height: 20%;
    width: 20%;
    margin-top: 20px;
  }
</style>
<%_   } _%>
<%_ } else { _%>
<%# -------------------- IS Using standard CSS -------------------- -%>
<style scoped>
  .message {
    color: #42b983;
  }

  Image {
    height: 20%;
    width: 20%;
    margin-top: 20px;
  }
</style>
<%_ } _%>