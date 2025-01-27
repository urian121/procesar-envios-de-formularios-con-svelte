<script>
  export let contactos = [];
  console.log(contactos);
</script>

<ul class="list-group list-group-flush">
  {#each contactos as contacto, i}
  <li class="list-group-item">
    <strong>{i + 1}. {contacto.nombre}</strong>  
    - Sexo: {contacto.sexo}, Profesión: {contacto.profesion}, Edad: {contacto.edad}
  </li>
  {/each}
</ul>
