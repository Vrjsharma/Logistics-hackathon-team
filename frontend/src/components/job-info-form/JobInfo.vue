<template>
  <div class="form-elements">
    <div class="row">

          <div class="flex xs12">
            <va-card :title="'Job Name'">
              <va-input
                  v-model="simple"
                  placeholder="Name of job"
                />
               </va-card>
          </div>
          <div class="flex xs12">
            <va-card :title="'Job Headline'">
              <va-input
                  v-model="withDescription"
                  placeholder="Headline of job"
                  :messages="messages"
                />
            </va-card>
          </div>

      <div class="medium-editor flex xs12">
          <va-card :title="$t('Job Description')">
            <div class="d-flex">
              <va-medium-editor
                @initialized="handleEditorInitialization"
                v-model="jobd"
              >
                <h1>Description about job</h1>
                <p>Describe here....</p>
              </va-medium-editor>
            </div>
          </va-card>
      </div>
       <div class="flex xs12">
          <va-card :title="$t('Do you live in sydney?')">
            <form>
              <div class="row">
                <div class="flex md6 xs12">
                    <va-select
                  :label="$t('forms.selects.multi')"
                  v-model="multiSelectModel"
                  textBy="description"
                  multiple
                  :options="simpleOptions"
                />
                </div>
              </div>
            </form>
          </va-card>
      </div>
      <div class="flex xs12">
        <va-card
          class="larger-padding"
        >
          <div class="row">
            <div class="flex">
              <va-button color="danger"> {{ 'Submit' }}</va-button>
            </div>
          </div>
        </va-card>
      </div>
    </div>
  </div>

</template>

<script>

export default {
  name: 'form-elements',
  data () {
    return {
      jobd: null,
      simpleOptions: ["Creating marketing materials","Social media content creation","Blogging/Writing","Real estate",
      "Construction","Bioinformatics","software analysis","statistical analysis","Law"],
      multiSelectModel: [],
      advancedList:[],
    }
  },
  methods: {
    clear (field) {
      this[field] = ''
    },
     handleEditorInitialization (editor) {
      this.editor = editor
      this.$nextTick(() => {
        this.highlightSampleText()
      })
    },
    highlightSampleText () {
      const sampleText = document.getElementsByClassName('default-selection')[0]
      this.editor.selectElement(sampleText)
    },
  },
}
</script>

<style>
  .row.row-inside {
    max-width: none;
  }
</style>
