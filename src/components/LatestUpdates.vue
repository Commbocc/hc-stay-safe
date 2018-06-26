<template lang="html">
  <div class="py-5 bg-white">
    <div class="container">
      <h2 class="text-center text-primary font-weight-bold font-serif" id="">
        {{ title }}
      </h2>

      <hr class="m-0">

      <div class="row">
        <div class="col-lg-5 col-md-6 order-md-12">

          <!-- HCFL ALert -->
          <div is="HcflAlert" class="my-3">
            HCFL Alert is Hillsborough County’s official mass notification system. It is designed to keep you informed about emergencies and certain non-emergency events in Hillsborough County.
          </div>

          <!-- Video -->
          <div v-if="true" class="embed-responsive embed-responsive-16by9 my-3">
            <iframe src="https://www.youtube.com/embed/oln1uC6JBwU?rel=0" class="embed-responsive-item" title="Video"></iframe>
          </div>

          <!-- social icons -->
          <ul class="list-inline text-center hide-external-indicator">
            <li v-for="social in socialIcons" class="list-inline-item px-1">
              <a :href="social.href" :title="social.name" class="text-secondary" target="_blank">
                <span :class="social.icon" class="fa-3x" :aria-label="social.name"></span>
              </a>
            </li>
          </ul>

          <hr class="mb-0">

        </div>
        <div class="col-lg-7 col-md-6">

          <!-- Latest Updates -->
          <div class="list-group list-group-flush hide-external-indicator">
            <a v-for="(post, index) in posts" :key="index" :href="post.link" target="_blank" class="list-group-item list-group-item-action">
              <div class="d-sm-flex flex-sm-row flex-md-column flex-lg-row">
                <div class="mr-sm-3 mr-md-0 mr-lg-3 d-flex flex-column text-center">
                  <span class="fas fa-bullhorn fa-2x text-primary"></span>
                  <small class="small text-muted my-3">
                    {{ post.date.format('lll') }}
                  </small>
                </div>
                <div class="media-body">
                  <h5 class="mt-0 mb-1 text-dark font-serif font-weight-bold">
                    {{ post.title }}
                  </h5>
                  {{ post.excerpt }}
                </div>
              </div>
            </a>
          </div>

        </div>
      </div>

    </div>
  </div>
</template>

<script>
import moment from 'moment'
import GoogleSheetModel from 'google-sheet-model'
import HcflAlert from './HcflAlert'

export default {
  extends: GoogleSheetModel,
  props: {
    title: {
      type: String,
      default: 'Latest Updates'
    },
    // google sheet model props
    sheetId: {
      default: '14c7p2JUfuRTC9JcbvG--pOu6IRtVuMZ7Flkv0EZ54Io'
    },
    tableId: {
      default: 4
    },
    fields: {
      default: () => ['date', 'title', 'link', 'excerpt']
    }
  },
  data () {
    return {
      socialIcons: [
        {
          name: 'Facebook',
          icon: 'fab fa-facebook',
          href: 'https://www.facebook.com/HillsboroughFL/'
        },
        {
          name: 'Twitter',
          icon: 'fab fa-twitter',
          href: 'https://twitter.com/HillsboroughFL'
        },
        {
          name: 'YouTube',
          icon: 'fab fa-youtube',
          href: 'https://www.youtube.com/user/HillsboroughCounty'
        }
      ]
    }
  },
  components: { HcflAlert },
  computed: {
    posts () {
      return this.instances.map(x => {
        x.date = moment(x.date, 'MM/DD/YYYY HH:mm:ss')
        return x
      })
    }
  }
}
</script>
