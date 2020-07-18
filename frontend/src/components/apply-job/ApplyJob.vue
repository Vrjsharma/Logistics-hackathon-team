<template>
  <div class="form-elements">
    <div class="row">
      <div class="offset--md6 flex xs12">
          <va-card :title="$t('Do you live in sydney?')">
            <form>
              <div class="row">
                <div class="flex md6 xs12">
                  <va-select
                    v-model="simpleSelectModel"
                    textBy="description"
                    :options="simpleOptions"
                  />
                </div>
              </div>
            </form>
          </va-card>
      </div>
      <div class="offset--md6 flex xs12">
        <va-card :title="'Let us know if you have any experience in these areas'">
          <div class="flex xs12">
            <va-card :title="$t('Creating Marketing Materials')">
              <va-rating
                v-model="value"
                size="large"
                color="info"
              />
            </va-card>
          </div>
          <div class="flex xs12">
            <va-card :title="$t('Social Media Content Creation')">
              <va-rating
                v-model="value1"
                size="large"
                color="info"
              />
            </va-card>
          </div>
          <div class="flex xs12">
            <va-card :title="$t('Blogging/Writing')">
              <va-rating
                v-model="value2"
                size="large"
                color="info"
              />
            </va-card>
          </div>
          <div class="flex xs12">
            <va-card :title="$t('Real Estate')">
              <va-rating
                v-model="value3"
                size="large"
                color="info"
              />
            </va-card>
          </div>
        </va-card>    
      </div>
      <div class="medium-editor offset--md6 flex xs12">
            <va-card :title="$t('pitch')">
              <div class="d-flex">
                <va-medium-editor
                  @initialized="handleEditorInitialization"
                >
                  <h1>Pitch Yourself!</h1>

                  <p>
                    Why should we hire you?
                  </p>
                </va-medium-editor>
              </div>
            </va-card>
      </div>
      <div class="medium-editor offset--md6 flex xs12">
          <va-card :title="$t('About you')">
            <div class="d-flex">
              <va-medium-editor
                @initialized="handleEditorInitialization"
              >
                <h1>Tell us about you - keep it interesting!!</h1>

                <p>
                  Your experience, hobbies, interests, even a fun fact!
                </p>
              </va-medium-editor>
            </div>
          </va-card>
      </div>
      <div class="offset--md6 flex xs12">
          <va-card :title="$t('Resume')">
            <va-file-upload
              dropzone
              v-model="advancedList"
            />
          </va-card>
        </div>
          <div class="offset--md6 flex xs12">
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
      value:0,
      value1:0,
      value2:0,
      value3:0,
      simpleOptions: [
        {
          id: 1,
          description: 'Yes',
        },
        {
          id: 2,
          description: 'No',
        },
        {
          id: 3,
          description: 'I have in the past',
        },
      ],
      simpleSelectModel: '',
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
