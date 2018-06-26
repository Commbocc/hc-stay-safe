<template lang="html">
  <div v-if="instances.length" class="list-group list-group-flush text-center mt-4">

    <div class="list-group-item py-2 d-flex justify-content-center align-items-center">
      <div class="px-3 w-50 text-right">
        Active Storm(s)
      </div>
      <strong class="px-3 w-50 text-left font-weight-bold">
        {{ current.storms }}
      </strong>
    </div>

    <div class="list-group-item py-2 d-flex justify-content-center align-items-center">
      <div class="px-3 w-50 text-right">
        <!-- evacLink -->
        <a :href="evacLink" class="text-white hide-external-indicator" target="_blank" :title="evacLabel" :aria-label="evacLabel">
          <span class="fas fa-info-circle mr-1" aria-hidden="true"></span>
          Evacuation Level(s)
        </a>
      </div>
      <strong class="px-3 w-50 text-left font-weight-bold">
        {{ current.evaclevels }}
      </strong>
    </div>

    <div class="list-group-item py-2 d-flex justify-content-center align-items-center">
      <div class="px-3 w-50 text-right">
        EOC Status
      </div>
      <strong class="px-3 w-50 text-left font-weight-bold">
        {{ current.eocstatus }}
      </strong>
    </div>

  </div>
</template>

<script>
import GoogleSheetModel from 'google-sheet-model'

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
    tableId: {
      default: 5
    },
    fields: {
      default: () => ['storms', 'evaclevels', 'eocstatus']
    }
  },
  computed: {
    current () {
      return this.instances[0]
    }
  }
}
</script>
