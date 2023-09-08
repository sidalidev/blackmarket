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
            name: "basket trouée",
            price: 6012.95,
            image: "https://media.istockphoto.com/id/1090985526/fr/photo/les-vieilles-chaussures-avec-des-trous-dans-les-orteils-us%C3%A9s.jpg?s=1024x1024&w=is&k=20&c=PtM1fe77gWUNJMyE7aatprTnXhMswcFyq9XkVlYNdZc=",
            stars: 4,
            blocked: false,
        },
    ]
</script>

<h1 class="text-center mt-8 text-2xl font-bold">Black Market 🩴</h1>

<div class="m-16">
    {#each products as product}
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
