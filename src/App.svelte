<script>
  import "bootstrap/dist/css/bootstrap.min.css";
  import Formulario from "./components/Formulario.svelte";
  import Contactos from "./components/Contactos.svelte";

  // Estado reactivo con $state
  let contactos = $state([]);

  // Función para actualizar el estado desde el hijo
  function addContacto(nuevoContacto) {
    // Actualizamos el estado con el nuevo contacto, usando el operador spread (...) para no mutar el estado directamente
    contactos = [...contactos, nuevoContacto];
  }
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
      <!-- Pasamos la función updateContactos como prop -->
      <Formulario updateContactos={addContacto} />
    </div>
    <div class="col-md-7">
      <h2 class="fw-bold text-center border-bottom mb-4">Datos ingresados</h2>
      <!-- Pasamos el estado contactos como prop -->
      <Contactos contactos={contactos} />
    </div>
  </div>
</div>