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
        label="ชื่อของคุณ *"
        hint="ชื่อและนามสกุล"
        lazy-rules
        :rules="[ val => val && val.length > 0 || 'กรุณาใส่ชื่อแนะนามสกุล']"
      />

      <q-input
        filled
        type="number"
        v-model="age"
        label="อายุของคุณ *"
        lazy-rules
        :rules="[
          val => val !== null && val !== '' || 'กรุณาใส่อายุของคุณ',
          val => val > 0 && val < 100 || 'มึงยังเป็นคนอยู่ไหม '
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
import { useQuasar } from 'quasar'
import { ref } from 'vue'

export default {
  setup () {
    const $q = useQuasar()

    const name = ref(null)
    const age = ref(null)
    const accept = ref(false)

    return {
      name,
      age,
      accept,

      onSubmit () {
        if (accept.value !== true) {
          $q.notify({
            color: 'red-5',
            textColor: 'white',
            icon: 'warning',
            message: 'You need to accept the license and terms first'
          })
        }
        else {
          $q.notify({
            color: 'green-4',
            textColor: 'white',
            icon: 'cloud_done',
            message: 'Submitted'
          })
        }
      },

      onReset () {
        name.value = null
        age.value = null
        accept.value = false
      }
    }
  }
}
</script>
