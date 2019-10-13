<template>
    <div>
        <div class="row no-gutters">
            <div class="col-12">
                <div class="card">
                    <div class="card-body">
                        <h5 class="card-title">Фильтры</h5>
                        <div class="card-text">
                            <form>
                                <div class="form-group">
                                    <select class="form-control" @change="returnFilter">
                                        <option value="all">Бренд</option>
                                        <option value="super">Super</option>
                                        <option value="puper">Puper</option>
                                        <option value="cool">Cool</option>
                                        <option value="like">Like</option>
                                    </select>
                                </div>
                                <div class="form-group">
                                    <select class="form-control" v-model="filterSize">
                                        <option value="all">Размер</option>
                                        <option value="29">29</option>
                                        <option value="31">31</option>
                                        <option value="35">35</option>
                                        <option value="37">37</option>
                                        <option value="42">42</option>
                                    </select>
                                </div>
                                <div class="form-group">
                                    <select class="form-control" v-model="filterColor">
                                        <option value="all">Цвет</option>
                                        <option value="синий">Синий</option>
                                        <option value="красный">Красный</option>
                                        <option value="зеленый">Зеленый</option>
                                        <option value="белый">Белый</option>
                                        <option value="серый">Серый</option>
                                    </select>
                                </div>
                                <div class="text-right">
                                    <a href="#" class="btn btn-sm btn-secondary">Сбросить</a>
                                </div>
                            </form>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import ProductList from '@/components/ProductList'
export default {
    methods: {
        returnFilter() {            
            this.$emit('updateFilter', {
                amount: 'this'     
            })
        }
    },
    props: ['filterBrand', 'filterSize', 'filterColor'],
}
</script>