<script>
  let data_form = [];
  let nombre = "";
  let sexo = "Masculino";
  let profesion = "";
  let edad = 18;

  function sendForm() {
    const data = {
      nombre,
      sexo,
      profesion,
      edad,
    };
    console.log(data);
    data_form.push(data);

    resetForm();
  }

  function resetForm() {
    nombre = "";
    sexo = "Masculino";
    profesion = "";
    edad = 18;
  }
</script>

<form on:submit|preventDefault={sendForm}>
  <div class="mb-3">
    <label for="Nombre" class="form-label">Nombre</label>
    <input type="text" name="nombre" bind:value={nombre} class="form-control" />
  </div>

  <div class="mb-3">
    <label for="Profesion" class="form-label">Profesión</label>
    <select
      class="form-select"
      name="profesion"
      bind:value={profesion}
      aria-label="Default select example"
    >
      <option selected>Seleccione</option>
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
      id="edadRange"
      min="18"
      max="60"
      bind:value={edad}
    />
  </div>

  <div class="container-fluid">
    <button type="submit" class="btn btn-primary w-100">
        Enviar Formulario
    </button>
  </div>
</form>
