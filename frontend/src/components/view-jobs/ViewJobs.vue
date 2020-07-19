<template>
  <div class="lists">
    <div class="row">
      <div class="flex lg12">
        <va-list fit class="mb-2">

          <va-list-label>
            {{ $t('Jobs') }}
          </va-list-label>

          <template v-for="(company) in companys">
            <va-item :key="'item' + company.id" clickable @click="notify(company.name)">

              <va-item-section avatar>
                <va-avatar>
                  <img :src="company.picture" :alt="company.name">
                </va-avatar>
              </va-item-section>

              <va-item-section>
                <va-item-label>
                  {{ company.name }}
                </va-item-label>

                <va-item-label caption>
                  {{ company.summary }}
                </va-item-label>
              </va-item-section>

              <va-item-section side>
                <va-button type="submit" clickable @click="onclick()" class="my-0">{{ $t('See job')}}</va-button>
              </va-item-section>
            </va-item>
          </template>
        </va-list>
      </div>


      </div>
    </div>
</template>

<script>
import data from './data.json'

export default {
  data () {
    return {
      companys: data.slice(0,4),
      appBanners: false,
      banners: false,
      notifications: true,
    }
  },
  methods: {
    notify (name) {
      this.showToast(`Clicked ${name}`, {
        position: 'bottom-right',
      })
    },
    onclick () {
      this.$router.push({ name: 'apply-job' })
    }
  },
}
</script>
