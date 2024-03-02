    <template>
    <v-container>
        <v-row>
        <v-col v-for="(product, index) in products" :key="index" cols="12" md="4">
            <v-card class="mb-4">
            <v-img :src="product.image" height="200px"></v-img>
            <v-card-title>{{ product.name }}</v-card-title>
            <v-card-subtitle>{{ product.price }}</v-card-subtitle>
            <v-card-text>{{ product.description }}</v-card-text>
            <v-card-actions>
                <v-btn color="primary" @click="addToCart(index)">Add to Cart</v-btn>
                <v-btn color="secondary">Details</v-btn>
            </v-card-actions>
            </v-card>
        </v-col>
        </v-row>
    </v-container>
    </template>

    <script>
    import Cookies from "js-cookie";

    export default {
    data() {
        return {
        products: [
            {
            name: "Cafe trung nguyên",
            price: "200,000 đ",
            description: "Description of Product 1",
            image: "https://via.placeholder.com/200",
            },
            {
            name: "cafe Phúc Long",
            price: "299,000 đ",
            description: "Cafe Phúc Long",
            image: "https://via.placeholder.com/200",
            },
            {
            name: "Combo quà tặng",
            price: "269,000 đ",
            description: "Cafe Phúc Long",
            image: "https://via.placeholder.com/200",
            },
            {
            name: "Combo quà tặng",
            price: "269,000 đ",
            description: "Cafe Phúc Long",
            image: "https://via.placeholder.com/200",
            },
            // Add more products as needed
        ],
        };
    },
    methods: {
        addToCart(index) {
        let cartItems = Cookies.get("cartItems") || "{}";

        cartItems = JSON.parse(cartItems);
        if (cartItems[index]) {
            cartItems[index]++;
        } else {
            cartItems[index] = 1;
        }

        // Store the updated cart items in cookies
        Cookies.set("cartItems", JSON.stringify(cartItems));
        this.$emit('addToCartEvent');

        },
        
    },
    };
    </script>

    <style></style>
