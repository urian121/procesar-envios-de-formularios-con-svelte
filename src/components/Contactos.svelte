<script>
  // Recibe la propiedad contactos desde el componente padre App.svelte
  let { contactos } = $props();
</script>

<div class="table-responsive">
  <table class="table table-striped table-hover">
    <thead>
      <tr>
        <th scope="col">#</th>
        <th scope="col">Nombre</th>
        <th scope="col">Sexo</th>
        <th scope="col">Profesión</th>
        <th scope="col">Edad</th>
        <th scope="col">Inglés</th>
      </tr>
    </thead>
    <tbody>
      {#each contactos as contacto, i}
        <tr>
          <td>{i + 1}</td>
          <td>{contacto.nombre}</td>
          <td>{contacto.sexo}</td>
          <td>{contacto.profesion}</td>
          <td>{contacto.edad}</td>
          <td>{contacto.ingles}</td>
        </tr>
      {/each}
    </tbody>
  </table>
</div>