<template>
    <div>
        <h1>{{ product.name }} -
            <span v-show="seeR">{{ (product.price * 97.41).toFixed(2) }} {{ rubli }}</span>
            <span v-show="seeD">{{ dollar }}{{ product.price }}</span>
        </h1>
        <h2>{{ available }}</h2>

        <button @click="addRubli">рубли</button>
        <button @click="addDollar">доллар</button>
    </div>
</template>

<script>
export default {
    name: 'ProductDetails',

    data() {
        return {
            seeR: 'руб',
            seeD: '',
            dollar: '$',
            product: {
                name: "Туфли",
                price: 99.99,
            },
            rubli: "рублей",
            available: "Available",
        };
    },

    mounted() {

    },

    methods: {
        addRubli() {
            this.seeD = ''
            this.seeR = 'руб'
        },
        addDollar() {
            this.seeR = ''
            this.seeD = 'долл'
        }

    },
    computed: {
        // eslint-disable-next-line vue/return-in-computed-property
        formattedPrice(see = this.seeR) {
            switch (see) {
                case 'руб':
                    this.addRubli
                    break;
                case 'долл':
                    this.addDollar
                    break;
            }
        }

    }
}

</script>

<style lang="scss" scoped></style>