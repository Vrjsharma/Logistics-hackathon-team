<template>
  <div class="form-elements">
    <div class="row offset--md6">
      <div class="flex xs12 sm6">
        <img src="https://randomuser.me/api/portraits/men/1.jpg">
      </div>
      <div class="flex xs12 sm6">
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
      <div class="flex xs12 sm6">
        <h1>Website Manager</h1>
        <br/><br/><br/>
        <p>Maintains and creates content for Bullis School’s website, with responsibilities for
technological aspects as well as site content. Additional responsibilities include ongoing
web strategy and overseeing website operation, with particular attention to design, content and
site maintenance. <br/> Updates website content, including information, images, calendar content,
schedules, graphics, etc., according to the changing needs of the School. <br/>Works with the
Executive Director of Institutional Advancement and the Communications Director, as well as
website designers and providers, to plan, maintain and improve online presence, initiating new
ways to enhance and develop the School’s website presence. <br/>This is primarily a telecommuting
position, however the website manager assists/attends Advancement meetings and events as
needed. </p>
      </div>
      <div class="flex xs12 sm6">
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
