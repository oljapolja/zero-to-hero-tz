<template>
    <div class="col-3">
        <div class="card text-center border-0 shadow-sm mb-3 bg-white rounded-lg" @click="showExtraInf(product)">
            <img :src="product.img" alt="alt" class="card-img-top">
            <div class="card-body p-1 m-1">
                <h5 class="card-title mb-0">{{product.name}}</h5>
                <div class="card-text">
                    <div>
                        <small class="card-text text-muted">
                            Категория
                        </small>
                    </div>
                    <div>
                        <del>{{product.oldPrice}}</del>
                        <strong>{{product.price}}</strong>
                    </div>
                    <div class="alert alert-dark p-0 m-0" role="alert" v-bind:class="{done:product.extraInf}">
                        <div>
                            <small>
                                <strong>Бренд</strong> {{product.brand}}
                            </small>
                        </div>
                        <div>
                            <small>
                                <strong>Размер</strong> {{product.size}}
                            </small>
                        </div>
                        <div>
                            <small>
                                <strong>Цвет</strong> {{product.color}}
                            </small>
                        </div>
                    </div>
                </div>
                <a href="#" class="btn btn-primary m-1" id="buy-button" @click.prevent.stop="purchaseAlert(product)">Купить</a>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        product: {
            type: Object
        }
    },
    methods: {
        purchaseAlert(product){
            alert(`Куплен товар ${product.name}`)
        },
        showExtraInf(product){
            product.extraInf = !product.extraInf;
        }
    }
}

</script>

<style>
.alert{
    display: none;
}

.done {
    display: inline-block;
}
</style>