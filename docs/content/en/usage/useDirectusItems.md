---
title: "useDirectusItems"
description: "Learn how to use Nuxt & Directus"
position: 10
category: "Usage"
---

> Check out the Directus [Items](https://docs.directus.io/reference/items/) documentation.

### `getItems`

Search for items in a specific collection, [`global search querys`](https://docs.directus.io/reference/query/) can be used

- **Arguments:**

  - data: [`DirectusItemRequest`](https://github.com/Intevel/nuxt-directus/blob/master/src/runtime/types/index.d.ts#L26)

- **Returns:** `Array`

```vue [pages/articles.vue]
<script setup lang="ts">
const { getItems } = useDirectusAuth();
const router = useRouter();

const fetchArticles = async () => {
  try {
    var filters = { content: "testcontent", title: "Test1" };
    var items = await getItems({
      collection: "News",
      params: {
        filter: filters,
      },
    });
  } catch (e) {}
};
</script>
```

### `getItemById`

Search for an item by id in a specific collection

- **Arguments:**

  - data: [`DirectusItemRequest`](https://github.com/Intevel/nuxt-directus/blob/master/src/runtime/types/index.d.ts#L26)

- **Returns:** `Object`

```vue [pages/article.vue]
<script setup lang="ts">
const { getItemById } = useDirectusAuth();

const fetchArticle = async () => {
  try {
    var item = await getItemById({
      collection: "News",
      id: "4776864a-75ee-4746-9ef4-bd5c2e38cc66",
    });
  } catch (e) {}
};
</script>
```