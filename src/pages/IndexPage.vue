<template>
  <q-page class="flex flex-center">
    <q-input
      v-model="inputVal"
      outlined
      label="Focus on me"
      style="width: 300px;"
      @focus="onFocus"
      @blur="onBlur"
    >
      <q-menu
        :model-value="popupOpen"
        no-parent-event
        fit
        no-focus
      >
        <q-card>
          <q-list padding>
            <q-item
              v-for="i in 5"
              :key="i"
              clickable
              dense
              @click="setVal(i)"
            >
              <q-item-section>
                <q-item-label>
                  {{ i }}
                </q-item-label>
              </q-item-section>
            </q-item>
          </q-list>
        </q-card>
      </q-menu>
    </q-input>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'
import sampleMixin from 'pages/sampleMixin'

export default defineComponent({
  name: 'IndexPage',
  mixins: [sampleMixin],
  data () {
    return {
      inputVal: '',
      popupOpen: false
    }
  },
  methods: {
    setVal (val) {
      this.inputVal = val
      this.$emit('sample')
    },
    onFocus () {
      this.popupOpen = true
    },
    onBlur () {
      this.popupOpen = false
    }
  }
})
</script>
