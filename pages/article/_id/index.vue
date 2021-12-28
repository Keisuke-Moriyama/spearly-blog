<template>
  <div>
    <h1>{{ fields.title.value }}</h1>
    <img alt="" :src="fields.image.value" />
    <div v-html="fields.description.value" />
    <div v-html="fields.date.value" />
  </div>
</template>
<script>
export default {
  async asyncData({ $axios, params }) {
      const responses = []
    responses.push($axios.get(
      `https://cms.spearly.app/api/v1/contents/${params.id}`,
      {
        headers: {
          Authorization:
            "Authorization: Bearer 2ASfB5F9kTxdHmhujEQkqfZruNhkoTTIR2-m-7xysH4"
        }
      }
    ));
    responses.push($axios.get(
      `https://cms.spearly.app/api/v1/forms/f-ZFUoK8OfIvlapA3RHGW2/latest`,
      {
        headers: {
          Authorization:
            "Authorization: Bearer 2ASfB5F9kTxdHmhujEQkqfZruNhkoTTIR2-m-7xysH4"
        }
      }
    ));
    const response = await Promise.all(responses)
    return { fields: response[0].data.fields };
  }
};
</script>
