<script setup>
import { onMounted } from 'vue';
import {
  BoxGeometry,
  Mesh,
  MeshBasicMaterial,
  PerspectiveCamera,
  Scene,
  WebGLRenderer
} from 'three';

onMounted(() => {
  // Get div for renderer
  const rendererDiv = document.getElementById('rendererDiv')

  const scene = new Scene();
  console.log(scene);
  const camera = new PerspectiveCamera( 75, window.innerWidth / window.innerHeight, 0.1, 1000 );
  console.log(camera);

  const renderer = new WebGLRenderer();
  renderer.setSize( 800,  600);
  rendererDiv.appendChild(renderer.domElement);

  const geometry = new BoxGeometry( 1, 1, 1 );
  const material = new MeshBasicMaterial( { color: 0x00ff00 } );
  const cube = new Mesh( geometry, material );
  scene.add( cube );

  camera.position.z = 5;

  function animate() {
    requestAnimationFrame( animate );
    renderer.render( scene, camera );
  }
  animate();
});


</script>

<template>
  <div id="rendererDiv">
  </div>
</template>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#rendererDiv {
  border: 1px solid black;
}
</style>
