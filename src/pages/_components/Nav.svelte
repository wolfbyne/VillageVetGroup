<script>
    import { totalAmount, itemCount } from '../store.js';

    function goCartTo(){
        location.href = '/checkout';
    }
</script>

<div class="container-fluid mt-3">
    <div class="text-center"><img src="https://res.cloudinary.com/splyce/image/upload/v1612031206/logos/cropped-new-banner12_latest_evsfwj.png" alt="Banner" class="img-fluid"></div>
    <nav class="navbar navbar-expand-lg navbar-light bg-transparent mt-2">
        <div class="container-fluid">
            <a class="navbar-brand" href="/">Village Vetshop</a>
            <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarSupportedContent">
                <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                    <li class="nav-item">
                        <a class="nav-link active" aria-current="page" href="/">Home</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" aria-current="page" href="/products">All products</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" aria-current="page" href="/checkout">Checkout</a>
                    </li>
                    <li class="nav-item">
                        <a class="nav-link" aria-current="page" href="https://villagevetgroup.co.za/about-us/">About</a>
                    </li>
                </ul>
                <div class="ml-5 align-items-center d-md-flex d-block flex-row mx-md-auto">
                    <a id="search-nav" class="nav-link" aria-current="page" href="/search"><i class="fas fa-search"></i> Search</a>
                </div>
                {#if $totalAmount > 0}
                    <form class="row row-cols-lg-auto g-3 align-items-center">
                        <div class="col-12">
                            <span>R {$totalAmount}.00</span>
                        </div>
                        <div class="col-12">
                            <span>{$itemCount}</span>
                        </div>
                    </form>
                {/if}
                <button on:click={goCartTo} class="btn btn-link nav-item d-flex">
                    <img src="https://res.cloudinary.com/splyce/image/upload/c_scale,h_40/v1611664806/logos/dog-food_umda72.png" alt="icon-cart"/>
                    <h6>View Bowl</h6>
                </button>
            </div>
        </div>
    </nav>
</div>