<script>
  // Importa Bootstrap y sus iconos
  import 'bootstrap/dist/css/bootstrap.min.css'
  import 'bootstrap-icons/font/bootstrap-icons.css'
  import Footer from './lib/Footer.svelte';
  import Api from './lib/Api.svelte';
</script>

 <!-- Botón del carrito -->
    <div class="position-relative">
      <a
        href="!#"
        class="btn btn_shopping cart-badge position-fixed top-0 end-0 me-4 mt-3 swing-on-hover border bg-white"
      >
        <i class="bi bi-bag-heart"></i>
        <span
          id="contador-carrito"
          class="position-absolute top-1 start-100 translate-middle badge rounded-pill bg-danger"
        >
          0
        </span>
      </a>
    </div>

     <div class="container my-5">
      <h1 class="text-center fw-bold">Bienvenidos a Tu Tienda de Café <i class="bi bi-cup-straw"></i></h1>
      <div class="row g-4 mt-4">
        <Api />
      </div>
    </div>



    <!-- Offcanvas del carrito -->
    <div
      class="offcanvas offcanvas-end"
      tabindex="-1"
      id="offcanvasRight"
      aria-labelledby="offcanvasRightLabel"
    >
      <div class="offcanvas-header border-bottom">
        <h4 class="offcanvas-title text-center">Carrito de compras</h4>
        <button
          type="button"
          class="btn-close"
          data-bs-dismiss="offcanvas"
          aria-label="Close"
        ></button>
      </div>

      <div class="offcanvas-body border-bottom"></div>

      <div class="offcanvas-footer mt-4">
        <h5 class="justify-content-between mb-2">
          <span class="fw-bold px-3">SUBTOTAL:</span>
          <span id="subtotal" class="fw-bold float-end px-2 fs-2"> $0.00 </span>
        </h5>
        <div class="text-center mb-5 px-3">
          <button class="btn btn-primary mt-5 w-100">
            Enviar pedido por WhatsApp
          </button>
        </div>
      </div>
    </div>

<Footer />