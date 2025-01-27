<script>
  import "bootstrap/dist/css/bootstrap.min.css";
  import Formulario from "./lib/Formulario.svelte";
  import Contactos from "./lib/Contactos.svelte";

  let contactos = []; // Este es el array de contactos que recibirá el hijo.
</script>

<div class="container mt-4">
  <div class="row justify-content-center">
    <div class="col-md-12 mb-5">
      <h1 class="text-center fw-bold">
        Procesar envíos de formularios HTML con Svelte
      </h1>
    </div>
  </div>

  <div class="row mt-5">
    <div class="col-md-5">
      <h1 class="fw-bold text-center border-bottom mb-4">
        Formulario de contacto
      </h1>
      <!-- Vinculamos la variable 'contactos' al hijo -->
      <Formulario bind:data_form={contactos} />
    </div>
    <div class="col-md-7">
      <h2 class="fw-bold text-center border-bottom mb-4">Datos ingresados</h2>
      <Contactos {contactos} />
    </div>
  </div>
</div>
