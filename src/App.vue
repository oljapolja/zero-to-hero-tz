<template>
  <div id="app" class="container-fluid">
    <h1>Список товаров</h1>
    <div class="row no-gutters">
      <div class="col-12">
        <div class="card">
          <div class="card-body">
            <h5 class="card-title">Фильтры</h5>
            <div class="card-text">
              <form>
                <div class="form-group">
                    <select class="form-control" v-model="filterBrand" @change="showAmount">
                        <option value="all">Бренд</option>
                        <option value="super">Super</option>
                        <option value="puper">Puper</option>
                        <option value="cool">Cool</option>
                        <option value="like">Like</option>
                    </select>
                </div>
                <div class="form-group">
                    <select class="form-control" v-model="filterSize" @change="showAmount">
                        <option value="all">Размер</option>
                        <option value="29">29</option>
                        <option value="31">31</option>
                        <option value="35">35</option>
                        <option value="37">37</option>
                        <option value="42">42</option>
                    </select>
                </div>
                <div class="form-group">
                    <select class="form-control" v-model="filterColor" @change="showAmount">
                        <option value="all">Цвет</option>
                        <option value="синий">Синий</option>
                        <option value="красный">Красный</option>
                        <option value="зеленый">Зеленый</option>
                        <option value="белый">Белый</option>
                        <option value="серый">Серый</option>
                    </select>
                </div>
                <div class="text-right">
                  <a href="#" class="btn btn-sm btn-secondary" @click="clear">Сбросить</a>
                </div>
              </form>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="alert alert-light" role="alert" ref="itemsAmount">
      Найдено {{filteredProducts.length}} товара
    </div>
    <ProductList 
      v-bind:products="filteredProducts"
    /> 
  </div>
</template>

<script>
import ProductList from '@/components/ProductList'
import ProductFilter from '@/components/ProductFilter'

export default {
  name: 'app',
  computed: {
    filteredProducts() {
      
      return this.products
      .filter(t => {
        return this.filterBrand === 'all' || this.filterBrand === t.brand;
      })
      .filter(t => {
        return this.filterSize === 'all' || this.filterSize == t.size;
      })
      .filter(t => {
        return this.filterColor === 'all' || this.filterColor == t.color;
      });;
    }
  },
  methods: {
    clear() {
      if (this.filterBrand !== 'all' || this.filterSize !== 'all' || this.filterColor !== 'all') {
        this.filterBrand = 'all';
        this.filterSize = 'all';
        this.filterColor = 'all';
      }
      this.showAmount();
    },
    showAmount() {
      if(this.filterBrand !== 'all' || this.filterSize !== 'all' || this.filterColor !== 'all') {
        this.$refs.itemsAmount.style.display = 'block';
      } else {
        this.$refs.itemsAmount.style.display = 'none';
      }
      
    }
  },
  data() {
    return {
      filterBrand: 'all',
      filterSize: 'all',
      filterColor: 'all',
      // filteredAmount: 4,
      products: [
        {
          id: 1,
          name: 'куртка красная',
          img: 'https://media.istockphoto.com/photos/male-coat-isolated-on-the-white-picture-id163208487',
          category: 'куртки',
          oldPrice: 5880,
          price: 4790,
          brand: 'super',
          size: 31,
          color: 'красный',
          extraInf: false
        },
        {
          id: 2,
          name: 'куртка большая',
          img: 'https://media.istockphoto.com/photos/red-womans-sports-jacket-picture-id520887025',
          category: 'куртки',
          oldPrice: 5900,
          price: 3790,
          brand: 'super',
          size: 42,
          color: 'зеленый',
          extraInf: false
        },
        {
          id: 3,
          name: 'куртка модная',
          img: 'https://media.istockphoto.com/photos/male-coat-isolated-on-the-white-picture-id163208487',
          category: 'куртки',
          price: 5550,
          brand: 'puper',
          size: 29,
          color: 'красный',
          extraInf: false
        },
        {
          id: 4,
          name: 'куртка выгодная',
          img: 'https://media.istockphoto.com/photos/red-womans-sports-jacket-picture-id520887025',
          category: 'куртки',
          oldPrice: 7900,
          price: 1990,
          brand: 'super',
          size: 29,
          color: 'зеленый',
          extraInf: false
        }
      ]
    }
  },
  components: {
    ProductList,
  },
}
</script>

<style>
</style>
