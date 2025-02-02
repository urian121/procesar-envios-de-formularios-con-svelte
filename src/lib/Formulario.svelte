<script>
  import { toast } from "nextjs-toast-notify";
  export let data_form = []; // Recibimos el array de contactos como un binding bidireccional

  let nombre = "";
  let sexo = "Masculino";
  let profesion = "";
  let edad = 18;
  let ingles = false;
  console.log(ingles);

  function sendForm() {
    const data = {
      nombre,
      sexo,
      profesion,
      edad,
      ingles : ingles ? "Sí" : "No",
    };
    console.log(data);

    // Creamos un nuevo array para forzar la actualización del binding
    data_form = [...data_form, data]; // Esto actualizará el array en el padre

    resetForm();

    // Mostramos la notificación
    toast.success("¡Fomulario enviado con éxito!", {
      duration: 5000,
      progress: true,
      position: "top-center",
      transition: "bounceIn",
      icon: '<svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.75" stroke-linecap="round" stroke-linejoin="round" class="lucide lucide-check"><path d="M20 6 9 17l-5-5"/></svg>',
      sonido: true,
    });

  }

  function resetForm() {
    nombre = "";
    sexo = "Masculino";
    profesion = "";
    edad = 18;
    ingles = false;
  }
</script>

<form on:submit|preventDefault={sendForm}>
  <div class="mb-3">
    <label for="Nombre" class="form-label">Nombre</label>
    <input
      type="text"
      name="nombre"
      bind:value={nombre}
      class="form-control"
      required
    />
  </div>

  <div class="mb-3">
    <label for="Profesion" class="form-label">Profesión</label>
    <select
      class="form-select"
      name="profesion"
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
        name="sexo"
        id="Masculino"
        value="Masculino"
        bind:group={sexo}
      />
      <label class="form-check-label" for="Masculino"> Masculino </label>
    </div>
    <div class="form-check">
      <input
        class="form-check-input"
        type="radio"
        name="sexo"
        bind:group={sexo}
        value="Femenino"
        id="Femenino"
      />
      <label class="form-check-label" for="Femenino"> Femenino </label>
    </div>
  </div>

  <div class="mb-3">
    <label for="edadRange" class="form-label">
      Edad: <span>{edad}</span> años
    </label>
    <input
      type="range"
      class="form-range"
      name="edad"
      id="edadRange"
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
      id="ingles"
      name="ingles"
      bind:checked={ingles}
    />
    <label class="form-check-label" for="ingles">
      {ingles ? 'Sí' : 'No'}
    </label>
  </div>
</div>

  <div class="container-fluid">
    <button type="submit" class="btn btn-primary w-100">
      Enviar Formulario
    </button>
  </div>
</form>
