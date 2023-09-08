<script>
    let products = [
        {
            warranty: 12,
            name: "Tonge petee",
            price: 331.98,
            image: "https://p0.storage.canalblog.com/06/15/460832/103582547_o.jpg",
            stars: 2,
            blocked: false,
        },

        {
            warranty: 24,
            name: "Unique chaussette",
            price: 23.48,
            image: "https://preview.redd.it/thats-one-weird-sock-v0-1o9os2rkcqbb1.jpg?width=640&crop=smart&auto=webp&s=091e38af2aceafab855bb5599c353b872c5533c3",
            stars: 4,
            blocked: true,
        },

        {
            warranty: 3,
            name: "Botte d'astronaute",
            price: 4500.51,
            image: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSN0zeJTmXezMEwv3-NfdZhSv5Dx0klTJctWLgKbwQlBqB9Jjrr26t-gaWxTRxyWKS5ZLU&usqp=CAU",
            stars: 4,
            blocked: false,
        },

        {
            warranty: 666,
            name: "Moustache satanique",
            price: 99.66,
            image: "https://m.media-amazon.com/images/I/71w56PHbE8L._AC_SL1100_.jpg",
            stars: 5,
            blocked: false,
        },
        {
            warranty: 5,
            name: "Capote de doigt",
            price: 2,
            image: "https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Flaboutiqueducool.com%2Fwp-content%2Fuploads%2F2022%2F05%2Fcapote-de-doigt-min.jpg&f=1&nofb=1&ipt=91f087f355e3baaa358efe64728c3ca5e405426e7b1853a1860011c7e2d6b9c2&ipo=images",
            stars: 2,
            blocked: false,
        },
    ]

    let order = "desc"

    $: sort_products = (products) => {
        let sorted_products = [...products]
        console.log("initial products", sorted_products)
        /*
         Pseudo code
         Parcours les index de la liste du 2e au dernier:
            tant que l'élément courant est inférieur à son voisin précédent et qu'on a pas ateint le début de la liste:
                intervertir l'élément courant avec son voisin de gauche

         */

        for (let idx = 1; idx < sorted_products.length; idx++) {
            let currentElement = sorted_products[idx]
            let prevIndex = idx - 1

            let calc_condition = (a, b) => {
                return order === "desc" ? a.price > b.price : a.price < b.price
            }
            while (
                prevIndex >= 0 &&
                calc_condition(currentElement, sorted_products[prevIndex])
            ) {
                console.log(
                    "currentElement",
                    currentElement,
                    "prevIndex",
                    sorted_products[prevIndex]
                )
                sorted_products[prevIndex + 1] = sorted_products[prevIndex]
                prevIndex = prevIndex - 1
            }
            sorted_products[prevIndex + 1] = currentElement
        }

        console.log("sorted products", sorted_products)
        return sorted_products
    }
    $: sorted_products = sort_products(products)
</script>

<h1 class="text-center mt-8 text-2xl font-bold">Black Market 🩴</h1>

<div class="flex justify-center mt-8">
    <button
        class="py-2 px-4 bg-cyan-800 text-white rounded-xl shadow-md hover:bg-cyan-600 transition-all hover:translate-x-1 hover:-translate-y-1 animate-bounce"
        on:click={() => {
            order = order === "asc" ? "desc" : "asc"
        }}
    >
        ️
        {order === "asc"
            ? "👆 Trier par prix croissant"
            : "👇 Trier par prix décroissant"}
    </button>
</div>

<div class="m-16">
    {#each sorted_products as product}
        <div
            class="flex items-center p-8 shadow rounded-xl my-5 cursor-pointer"
        >
            <img class="w-24 h-24 rounded-xl" src={product.image} alt="" />
            <div class="ml-8 text-gray-500 text-sm">
                <p class="font-bold text-black">{product.name}</p>
                <p>{!product.blocked ? "Débloqué" : "Bloqué"}</p>
                <p>Garantie commerciale: {product.warranty} mois</p>
                <div class="flex w-16">
                    {#each Array(product.stars) as _, i}
                        <p class="mr-1">⭐️</p>
                    {/each}
                </div>
                <p class="text-black">À partir de: {product.price} €</p>
            </div>
        </div>
    {/each}
</div>
