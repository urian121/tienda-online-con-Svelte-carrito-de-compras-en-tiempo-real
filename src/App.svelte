<script>
  import "bootstrap/dist/css/bootstrap.min.css";
  import "bootstrap-icons/font/bootstrap-icons.css";
  import "bootstrap/dist/js/bootstrap.bundle.min.js"; // Asegúrate de importar Bootstrap JS

  import "./css/global.css";

  import Footer from "./lib/Footer.svelte";
  import Api from "./lib/Api.svelte";
  import { cart, removeFromCart } from "./stores/cartStore";

  function calculateSubtotal() {
    return $cart
      .reduce((total, item) => total + item.price * item.quantity, 0)
      .toFixed(2);
  }

  function mostrarOcultarOffcanvas() {
    const offcanvasElement = document.getElementById("offcanvasRight");
    const btn_shopping = document.querySelector(".btn_shopping");

    // Toggle para mostrar/ocultar el offcanvas
    let show = offcanvasElement.classList.toggle("show");
    if (!show) {
      toggleOffcanvas(false);
    }

    // Añadir la clase de animación al botón
    btn_shopping.classList.add("balanceo");

    // Eliminar el efecto de balanceo después de 500ms
    setTimeout(() => {
      btn_shopping.classList.remove("balanceo");
    }, 500);
  }

  function closeOffcanvas() {
    const offcanvasElement = document.getElementById("offcanvasRight");
    offcanvasElement.classList.remove("show");

    // Mostrar el carrito si 'show' es true, ocultarlo si es false
    toggleOffcanvas(false);
  }

  /**
   * Muestra u oculta el offcanvas del carrito
   * @param {boolean} show
   */
  function toggleOffcanvas(show) {
    const offcanvas = document.querySelector(".offcanvas");
    // Añadir transiciones para el efecto visual de apertura/cierre
    offcanvas.classList.add("transition");

    // Mostrar el carrito si 'show' es true, ocultarlo si es false
    if (show) {
      offcanvas.classList.add("show");
    } else {
      offcanvas.classList.remove("show");
      offcanvas.classList.add("hiding");
      setTimeout(() => offcanvas.classList.remove("hiding"), 600);
    }
  }

  function generateWhatsAppMessage() {
    // Construir el mensaje con los productos del carrito
    const cartItems = $cart
      .map((item) => {
        return `${item.name} - ${item.quantity} x $${item.price}`;
      })
      .join("\n"); // Une todos los productos con salto de línea

    const subtotal = calculateSubtotal();
    const message = `¡Hola! Quiero hacer el siguiente pedido:\n\n${cartItems}\n\nSubtotal: $${subtotal}\n\n¡Gracias!`;

    // Codificar el mensaje para usarlo en una URL
    return encodeURIComponent(message);
  }

  // Mostrar el carrito en la consola
  // $: console.log($cart);
</script>

<!-- Botón del carrito -->
<div class="position-relative">
  <a
    href="!#"
    class="btn btn_shopping cart-badge position-fixed top-0 end-0 me-4 mt-3 swing-on-hover border bg-white"
    aria-label="Carrito de compras"
    on:click={mostrarOcultarOffcanvas}
  >
    <i class="bi bi-bag-heart"></i>
    <span
      id="contador-carrito"
      class="position-absolute top-1 start-100 translate-middle badge rounded-pill bg-danger"
    >
      {$cart.length}
    </span>
  </a>
</div>

<!-- Contenido principal -->
<div class="container my-5">
  <h1 class="text-center fw-bold">
    Bienvenidos a Tu Tienda de Café <i class="bi bi-cup-straw"></i>
  </h1>
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
      on:click={closeOffcanvas}
    ></button>
  </div>

  <div class="offcanvas-body border-bottom">
    <div class="container mb-3">
      {#if $cart.length > 0}
        {#each $cart as item}
          <div class="row align-items-center border-bottom py-2">
            <div class="col-3">
              <img
                class="img-fluid rounded"
                src="./fotos-cafe/{item.image}.jpg"
                alt={item.name}
              />
            </div>
            <div class="col-6">
              <h6 class="mb-1 title-product">{item.name}</h6>
              <p class="mb-0 detalles-product">{item.category}</p>
            </div>

            <div class="col-3 text-end">
              <span class="fw-bold"
                ><span class="fs-6 color-gris">{item.quantity}x</span><span
                  class="fs-5 precio">${item.price}</span
                ></span
              >
              <button
                class="btn btn-danger mt-2 btn-borrar"
                aria-label="Borrar"
                on:click={() => removeFromCart(item.id)}
                ><i class="bi bi-trash3"></i></button
              >
            </div>
          </div>
        {/each}
      {:else}
        <p class="text-center">No hay productos en el carrito.</p>
      {/if}
    </div>
  </div>

  <div class="offcanvas-footer mt-4">
    <h5 class="justify-content-between mb-2">
      <span class="fw-bold px-3">SUBTOTAL:</span>
      <span id="subtotal" class="fw-bold float-end px-2 fs-2"
        >${calculateSubtotal()}</span
      >
    </h5>
    <div class="text-center mb-5 px-3">
      <button
        class="btn btn-primary mt-5 w-100"
        on:click={() => {
          const message = generateWhatsAppMessage();
          const phoneNumber = "+573213872648";
          const url = `https://wa.me/${phoneNumber}?text=${message}`;
          window.open(url, "_blank");
        }}
      >
        Enviar pedido por WhatsApp
      </button>
    </div>
  </div>
</div>

<Footer />
