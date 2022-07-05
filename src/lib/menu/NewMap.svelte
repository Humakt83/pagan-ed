<script>
  import { createEventDispatcher } from 'svelte';
  import Button from '../Button.svelte'

  const dispatch = createEventDispatcher();

  const newMap = (size) => dispatch('newmap', {size})
</script>

<main>
  <Button buttonFn={() => newMap(32)} buttonName={'Tiny (32x32)'} />
  <Button buttonFn={() => newMap(64)} buttonName={'Small (64x64)'} />
  <Button buttonFn={() => newMap(128)} buttonName={'Medium (128x128)'} />
  <Button buttonFn={() => newMap(256)} buttonName={'Large (256x256)'} />
  <Button buttonFn={() => newMap(512)} buttonName={'Huge (512x512)'} />
</main>