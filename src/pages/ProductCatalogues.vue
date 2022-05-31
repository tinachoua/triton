<template>
  <q-page class="q-pa-sm">
    <div>
      <q-card class="no-border no-shadow bg-transparent">
        <q-card-section class="q-pa-sm">
          <q-input rounded v-model="search" outlined placeholder="Search Product">
            <template v-slot:append>
              <q-icon v-if="search === ''" name="search"/>
              <q-icon v-else name="clear" class="cursor-pointer" @click="search = ''"/>
            </template>
          </q-input>
        </q-card-section>
      </q-card>
    </div>
    <div class="row q-col-gutter-sm ">
      <div class="col-md-4 col-lg-4 col-sm-12 col-xs-12" v-for="item, item_index in data">
        <card-product :data="item"></card-product>
      </div>
    </div>
  </q-page>
</template>

<script>
import {defineComponent, defineAsyncComponent} from 'vue';
import {ref} from 'vue';

const data = [
  {
    title: 'Mini series',
    caption: 'M1',
    rating: 2,
    amount: '$599',
    img: require('../assets/products/s1.png'),
    chip: 'Discount 90%',
    chip_color: 'grey-4',
    chip_class: 'text-blue absolute-top-right'
  },
  {
    title: 'MegaEdge', // 人工智慧推論運算平台
    caption: 'AIP-FH31-A1',
    rating: 4,
    amount: '$1599',
    img: require('../assets/products/AIPFH31A1.png'),
  },
  {
    title: 'Platform Series',
    caption: 'AX720-X32',
    rating: 1,
    amount: '$599',
    img: require('../assets/products/AX720X32.png'),
    chip: 'Sold Out',
    chip_color: 'grey-8',
    chip_class: 'text-white absolute-top-right'
  },
  {
    title: 'SuperEdge',
    caption: 'AIS-D422-A1',
    rating: 5,
    amount: '$20799',
    img: require('../assets/products/AISD422A1.png'),
    chip: 'Discount 80%',
    chip_color: 'grey-4',
    chip_class: 'text-blue absolute-top-right'
  },
  {
    title: 'Platform Series',
    caption: 'AN810-XNX',
    rating: 2,
    amount: '$599',
    img: require('../assets/products/AN810XNX.png'),
  },
  {
    title: 'Platform Series',
    caption: 'AN110-XNX',
    rating: 4,
    amount: '$399',
    img: require('../assets/products/AN110XNX.png'),
  },
];

export default defineComponent({
  name: "ProductCatalogues",
  components: {CardProduct: defineAsyncComponent(() => import('components/cards/CardProduct'))},
  setup() {
    const search = ref('');
    return {
      search,
      data
    }
  }
})
</script>

<style scoped>

</style>
