<script>
  // Importamos la función toast de nextjs-toast-notify
  import { toast } from "nextjs-toast-notify";

// Recibe la función updateContactos como prop desde el componente padre.
let { updateContactos } = $props();

/**
 * Estados reactivos para los campos del formulario.
 * Se inicializan con valores por defecto.
 */
let nombre = $state("");
let sexo = $state("Masculino");
let profesion = $state("");
let edad = $state(18);
let ingles = $state(false);

// Maneja el envío del formulario, previene el comportamiento predeterminado y actualiza los contactos.
function sendForm(event) {
    event.preventDefault(); // Previene el comportamiento predeterminado del formulario

    // Objeto con los datos del formulario
    const data = {
      nombre,
      sexo,
      profesion,
      edad,
      ingles: ingles ? "Sí 😊" : "No 😭",
    };
  console.log(data);

    // Actualiza el estado de los contactos en el componente padre. 
    updateContactos(data);
    resetForm(); // Limpia los campos del formulario

    // Llama a la función miToast para mostrar un mensaje de éxito.
    miToast();
  }

  // Muestra un mensaje de éxito al enviar el formulario.
  function miToast() {
    toast.success("¡Formulario enviado con éxito!", {
      duration: 5000,
      progress: true,
      position: "top-center",
      transition: "bounceIn",
      icon: "",
      sound: true,
    });
  }


  // Limpia los campos del formulario.
  function resetForm() {
    nombre = "";
    sexo = "Masculino";
    profesion = "";
    edad = 18;
    ingles = false;
  }
</script>

<!-- Formulario de contacto con el evento onsubmit para manejar el envío del formulario   -->
<form onsubmit={sendForm}>
  <div class="mb-3">
    <label for="Nombre" class="form-label">Nombre</label>
    <input
      type="text"
      bind:value={nombre}
      class="form-control"
      required
    />
  </div>

  <div class="mb-3">
    <label for="Profesion" class="form-label">Profesión</label>
    <select
      class="form-select"
      bind:value={profesion}
      aria-label="Default select example"
      required
    >
      <option value="Ingeniero de software">Ingeniero de software</option>
      <option value="Programador Senior">Programador</option>
      <option value="Full Stack">Full Stack</option>
    </select>
  </div>

  <div class="mb-3">
    <label for="Sexo" class="form-label">Sexo</label>
    <div class="form-check">
      <input
        class="form-check-input"
        type="radio"
        value="Masculino"
        bind:group={sexo}
      />
      <label class="form-check-label" for="Masculino">Masculino</label>
    </div>
    <div class="form-check">
      <input
        class="form-check-input"
        type="radio"
        value="Femenino"
        bind:group={sexo}
      />
      <label class="form-check-label" for="Femenino">Femenino</label>
    </div>
  </div>

  <div class="mb-3">
    <label for="edadRange" class="form-label">
      Edad: <span>{edad}</span> años
    </label>
    <input
      type="range"
      class="form-range"
      min="18"
      max="60"
      bind:value={edad}
    />
  </div>

  <div class="mb-3">
    <label for="Ingles">¿Habla inglés?</label>
    <div class="form-check form-switch">
      <input
        class="form-check-input"
        type="checkbox"
        role="switch"
        bind:checked={ingles}
      />
      <label class="form-check-label" for="ingles">
        {ingles ? "Sí" : "No"}
      </label>
    </div>
  </div>

  <div class="container-fluid">
    <button type="submit" class="btn btn-primary w-100">
      Enviar Formulario
    </button>
  </div>
</form>