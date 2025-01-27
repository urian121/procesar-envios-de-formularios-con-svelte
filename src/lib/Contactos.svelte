<script>
  export let contactos = [];
  console.log(contactos);
</script>

<ul class="list-group list-group-flush">
  {#each contactos as contacto, i}
    <li class="list-group-item">
      {i + 1}. <span class="fw-bold">Nombre:</span>
      {contacto.nombre} - <span class="fw-bold">Sexo:</span>
      {contacto.sexo}, <span class="fw-bold">Profesión:</span>
      {contacto.profesion}, <span class="fw-bold">Edad:</span>
      {contacto.edad} - <span class="fw-bold">Ingles:</span>{contacto.ingles}
    </li>
  {/each}
</ul>

<style>
  li {
    display: flex;
    justify-content: space-around;
  }
</style>
