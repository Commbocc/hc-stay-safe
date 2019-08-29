<template lang="html">
  <div class="card mb-3">

    <div class="card-header">
      <h4 class="cared-title text-center">Operational Status</h4>
    </div>

    <div v-if="instances.length" class="list-group list-group-flush rounded-0 mb-0">

      <div class="list-group-item rounded-0 py-2 d-flex justify-content-center align-items-center">
        <div class="px-3 w-50 text-right">
          Active Storm(s)
        </div>
        <strong class="px-3 w-50 text-left font-weight-bold">
          {{ current.storms }}
        </strong>
      </div>

      <div class="list-group-item rounded-0 py-2 d-flex justify-content-center align-items-center">
        <div class="px-3 w-50 text-right">
          <!-- evacLink -->
          <a :href="evacLink" class="text-primary hide-external-indicator" target="_blank" :title="evacLabel" :aria-label="evacLabel">
            <span class="fas fa-info-circle mr-1" aria-hidden="true"></span>
            Evacuation Level(s)
          </a>
        </div>
        <strong class="px-3 w-50 text-left font-weight-bold">
          {{ current.evaclevels }}
        </strong>
      </div>

      <div class="list-group-item rounded-0 py-2 d-flex justify-content-center align-items-center">
        <div class="px-3 w-50 text-right">
          EOC Status
        </div>
        <strong class="px-3 w-50 text-left font-weight-bold">
          {{ current.eocstatus }}
        </strong>
      </div>

    </div>

  </div>
</template>

<script>
import GoogleSheetModel from '@hcflgov/vue-google-sheet-model'

export default {
  name: 'OperationalStatus',
  extends: GoogleSheetModel,
  props: {
    title: {
      type: String,
      default: 'Operational Status'
    },
    evacLabel: {
      type: String,
      default: 'Find Evacuation Zone'
    },
    evacLink: {
      type: String,
      default: 'https://maps.hillsboroughcounty.org/HEAT/HEAT.html'
    },
    // google sheet model props
    sheetId: {
      default: '14c7p2JUfuRTC9JcbvG--pOu6IRtVuMZ7Flkv0EZ54Io'
    },
    tableIndex: {
      default: 5
    }
  },
  computed: {
    current () {
      return this.instances[0]
    }
  }
}
</script>
