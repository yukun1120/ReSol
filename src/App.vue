<script setup lang="ts">
import {reactive, provide} from "vue";
import {RouterView} from "vue-router";
// vue-routerをインポートすることで<RouterView>が使える
import type {Member} from "@/interfaces";
// 外部モジュールで定義された方をインんポートする場合は、import typeとする必要がある
// srcフォルダを示す記法 相対パスではメンテナンス性が低下する

const memberList = new Map<number, Member>();
memberList.set(33456,{id:33456, name: "田中太郎", email: "bow@example.com", points:35, note: "初回入会特典あり。"});
memberList.set(47783,{id:47783, name: "田中太郎", email: "bow@example.com", points:35});
provide("memberList", reactive(memberList));
</script>

<template>
  <header>
    <H1>Vue Routerサンプル</H1>
  </header>
  <main>
    <RouterView/>
  </main>
</template>

<style scoped>
  main {
    border: blue 1px solid;
    padding: 10px;
  }
  #breadcrumbs ul li {
    display: inline;
    list-style-type: none;
  }
  #breadcrumbs {
    margin-left: 0px;
  }

  #breadcrumbs ul {
    padding-left: 0px;
    padding-inline-start: 0px;
  }
  #breadcrumbs ul .current {
    color: red;
  }
  #breadcrumbs ul li:before {
    content: ">";
  }
  #breadcrumbs ul li:first-child:before {
    content: none;
  }
</style>
