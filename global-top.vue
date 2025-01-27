<template>
  <div></div>
</template>

<script setup lang="ts">
import { onMounted } from "vue";

const MAX_PAGE = 10;

onMounted(() => {
  // 一定時間ごとにページを切り替える
  const cycle = (page) => {
    $slidev.nav.go(page);
    // 長めに表示するページ
    // ページごとの表示時間
    const LONG_VIEW_PAGES = [
      1, // トップ
      2, // ハッシュタグ
      3, // ご案内
      4, // 懇親会について
      5, // 注意事項
    ];
    const TIME_NORMAL_MS = 6000;
    const TIME_LONG_MS = 10000;
    setTimeout(
      () => cycle((page % MAX_PAGE) + 1),
      LONG_VIEW_PAGES.includes(page) ? TIME_LONG_MS : TIME_NORMAL_MS
    );
  };
  cycle(1);
});
</script>
