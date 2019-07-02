<script>
import { mapState } from 'vuex'

export default {
  props: {
    opened: {
      type: Boolean,
      default: false
    },
  },
  data () {
    return {}
  },
  computed: {
    ...mapState([
      'style',
    ]),
  },
  methods: {
    confirm () { this.$emit('confirm') },
    cancel () { this.$emit('cancel') },
  },
}
</script>

<template>
  <QDialog
    :value="opened"
    :maximized="$q.screen.lt.sm"
    transition-show="slide-top"
    transition-hide="slide-bottom"
  >
    <QCard>
      <AppContent
        tag="QCardSection"
        class="text-h6 q-mx-md"
        entry="user"
        field="account.reverse_search_prerequisite_header"
      />

      <QCardSection class="q-ma-md">
        <slot>
          <AppContent entry="user" field="account.reverse_search_prerequisite_message" />
        </slot>
      </QCardSection>

      <QCardSection class="row justify-between">
        <slot name="action">
          <QBtn
            flat
            :rounded="style.roundedTheme"
            color="primary"
            @click="cancel"
          >
            <AppContent entry="navigation" field="close" />
          </QBtn>
          <QBtn
            :rounded="style.roundedTheme"
            color="secondary"
            @click="confirm"
          >
            <AppContent entry="payment" field="subscription.subscribe_label" />
          </QBtn>
        </slot>
      </QCardSection>
    </QCard>
  </QDialog>
</template>

<style lang="stylus" scoped>

</style>
