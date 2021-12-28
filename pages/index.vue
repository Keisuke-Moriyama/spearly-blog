<template>
  <div>
    <ul>
      <li v-for="(content, index) in contents" :key="index">
        <!-- <img alt="" :src="content.fields.image.value" /> -->
        <nuxt-link :to="`/article/${content.public_uid}`">{{
          content.fields.title.value
        }}</nuxt-link>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  async asyncData({ $axios }) {
    const response = await $axios.get(
      "https://cms.spearly.app/api/v1/content_types/ct-sabl3PON4SyIUtM6QWZr/contents",
      {
        headers: {
          Authorization:
            "Authorization: Bearer 2ASfB5F9kTxdHmhujEQkqfZruNhkoTTIR2-m-7xysH4"
        }
      }
    );
    return { contents: response.data.contents };
  }
};
</script>
