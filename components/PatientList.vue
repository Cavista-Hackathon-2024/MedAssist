<template>
  <div class="card">
    <DataTable :value="products" tableStyle="min-width: 50rem">
      <template #header>
        <div
          class="flex flex-wrap align-items-center justify-content-between gap-2"
        >
          <span class="text-xl text-900 font-bold">Patients Database</span>
        </div>
      </template>
      <Column header="Image">
        <template #body="slotProps">
          <img
            src="@/assets/images/profile.png"
            :alt="slotProps.data.image"
            class="w-6rem border-round"
          />
        </template>
      </Column>
      <Column field="name" header="Name"></Column>
      <Column field="price" header="Patient ID">
        <template #body="slotProps">
          {{ formatCurrency(slotProps.data.price) }}
        </template>
      </Column>
      <Column field="category" header="Medical Record Number"></Column>
      <Column header="Status">
        <template #body="slotProps">
          <Tag
            :value="slotProps.data.inventoryStatus"
            :severity="getSeverity(slotProps.data)"
          />
        </template>
      </Column>
      <template #footer>
        <i>Truncated list for Demo purposes</i>
      </template>
    </DataTable>
  </div>
</template>

<script setup>
const products = ref();
products.value = [
  {
    id: "1000",
    name: "Ogunsola Abosede",
    image: "bamboo-watch.jpg",
    price: 'OGA-2024-001',
    category: "Accessories",
    quantity: 24,
    inventoryStatus: "IN-PATIENT",
    rating: 5,
  },
  {
    id: "1001",
    name: "Adaeze Ngozi",
    description: "Product Description",
    image: "black-watch.jpg",
    price: 'ADN-2024-004',
    category: "Accessories",
    quantity: 61,
    inventoryStatus: "OUT-PATIENT",
    rating: 4,
  },
  {
    id: "1002",
    name: "Ifeoma Adebayo",
    description: "Product Description",
    image: "blue-band.jpg",
    price: 'IFA-2024-003',
    category: "Fitness",
    quantity: 2,
    inventoryStatus: "IN-PATIENT",
    rating: 3,
  },
  {
    id: "1003",
    name: "Ngozi Nwosu",
    description: "Product Description",
    image: "blue-t-shirt.jpg",
    price: 'NNW-2024-002',
    category: "Clothing",
    quantity: 25,
    inventoryStatus: "IN-PATIENT",
    rating: 5,
  },
];

const formatCurrency = (value) => {
  return value.toLocaleString("en-US", { style: "currency", currency: "USD" });
};
const getSeverity = (product) => {
  switch (product.inventoryStatus) {
    case "OUT-PATIENT":
      return "success";

    case "IN-PATIENT":
      return "warning";

    default:
      return null;
  }
};
</script>

<style scoped lang="less">
.card {
    margin-top: 50px;
}
img {
    width: 100px;
    height: 100px;
    border-radius: 100%;
}
</style>
