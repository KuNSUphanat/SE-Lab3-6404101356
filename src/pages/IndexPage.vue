<template>
  <div class="q-pa-md q-gutter-sm">

<q-bar>
  <div class="cursor-pointer">File</div>
  <div class="cursor-pointer">Edit</div>
  <div class="cursor-pointer gt-xs">View</div>
  <div class="cursor-pointer gt-xs">Window</div>
  <div class="cursor-pointer">Help</div>
  <q-space />
  <q-btn dense flat icon="minimize" />
  <q-btn dense flat icon="crop_square" />
  <q-btn dense flat icon="close" />
</q-bar>

<q-bar class="bg-black text-white">
  <div class="cursor-pointer">File</div>
  <div class="cursor-pointer">Edit</div>
  <div class="cursor-pointer gt-xs">View</div>
  <div class="cursor-pointer gt-xs">Window</div>
  <div class="cursor-pointer">Help</div>
  <q-space />
  <q-btn dense flat icon="minimize" />
  <q-btn dense flat icon="crop_square" />
  <q-btn dense flat icon="close" />
</q-bar>

</div>

  <div class="q-pa-md" style="max-width: 400px">

    <q-form
      @submit="onSubmit"
      @reset="onReset"
      class="q-gutter-md"
    >
      <q-input
        filled
        v-model="name"
        label="Your name *"
        hint="Name and surname"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'Please type something']"
      />

      <q-input
        filled
        type="number"
        v-model="age"
        label="Your age *"
        lazy-rules
        :rules="[
          val => val !== null && val !== '' || 'Please type your age',
          val => val > 0 && val < 100 || 'Please type a real age'
        ]"
      />

      <q-toggle v-model="accept" label="I accept the license and terms" />

      <div>
        <q-btn label="Submit" type="submit" color="primary"/>
        <q-btn label="Reset" type="reset" color="primary" flat class="q-ml-sm" />
      </div>
    </q-form>

  </div>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'IndexPage'
})
</script>
