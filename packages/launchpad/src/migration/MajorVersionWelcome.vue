<!--
  MajorVersionWelcome.vue

  This is the landing page that all users will see when they upgrade
  to a new major version.

  See the README of this package for details about this component.

  Internal Cypress employees: the process around managing this content
  is documented in `prod-eng-docs`. Refer to those docs when modifying
  this component or reviewing changes. Changes should go through
  a specific approval process.
 -->

<template>
  <div class="bg-no-repeat bg-cover h-screen min-h-[700px] lp-wrapper">
    <div
      ref="wrapper"
      class="rounded mx-auto bg-gray-50/50 border-[rgba(0,0,0,0.05)] border-[4px] max-w-[80vw] top-[7vh] w-[716px] relative overflow-hidden"
    >
      <div
        ref="scroller"
        class="bg-white rounded-b max-h-[72vh] pb-[90px] overflow-scroll"
      >
        <div class="h-full">
          <div
            class="p-[16px]"
            data-cy="release-highlights"
          >
            <h1 class="font-medium text-center mb-[8px] tracking-tighter text-[22px] leading-snug text-gray-1000">
              {{ t('majorVersionWelcome.title') }}
            </h1>

            <div
              v-if="slots['video']"
              class="border-transparent rounded mb-6 bg-gray-50/50 border-4px text-center max-w-80vw w-688px overflow-hidden"
            >
              <div
                class="bg-white rounded-t border-4px-gray-500 w-full p-24px"
                data-cy="video-container"
              >
                <slot name="video" />
              </div>
            </div>

            <div class="mb-[16px]">
              <ExternalLink
                href="https://on.cypress.io/changelog?utm_source=Binary%3A+App&utm_medium=splash-page&utm_campaign=v13#13-0-0"
                class="font-bold text-indigo-500"
              >
                13.0.0
              </ExternalLink>
              <span class="font-light pl-[10px] text-gray-500 text-[14px]">
                Released {{ versionReleaseDates['13'] }}
              </span>
            </div>
            <div class="children:mb-[16px]">
              <p>
                For a complete list of updates please review our
                <ExternalLink href="https://on.cypress.io/changelog?utm_source=Binary%3A+App&utm_medium=splash-page&utm_campaign=v13#13-0-0">
                  <!--eslint-disable-next-line vue/multiline-html-element-content-newline-->
                  changelog</ExternalLink>. To take a deep-dive into this release, read our <ExternalLink href="https://on.cypress.io/cypress-13-release?utm_source=Binary%3A+App&utm_medium=splash-page&utm_campaign=v13#13-0-0">
                  <!--eslint-disable-next-line vue/multiline-html-element-content-newline-->
                  blog post</ExternalLink>.
              </p>

              <h2 class="font-bold text-[18px] text-jade-1000">
                Test Replay
              </h2>

              <p>
                Test Replay brings the debugging experience you know and love from the Cypress app directly into your recorded tests in Cypress Cloud. Previously, trying to debug failures and flake in CI was painful and time consuming with only videos & screenshots. Test Replay provides a way to inspect the DOM, network events, and console logs of your application from your tests exactly as they ran in CI.
              </p>

              <p>
                Test Replay is available in all Cypress Cloud plans. To start using Test Replay, simply record a run to Cypress Cloud. Learn more in our <ExternalLink href="https://on.cypress.io/test-replay?utm_source=Binary%3A+App&utm_medium=splash-page&utm_campaign=v13#13-0-0">
                  <!--eslint-disable-next-line vue/multiline-html-element-content-newline-->
                  documentation</ExternalLink>.
              </p>

              <h2 class="font-bold mt-[24px] mb-[16px] text-[18px] text-jade-1000">
                Changes to video defaults
              </h2>

              <p>
                <InlineCodeFragment>video</InlineCodeFragment> and <InlineCodeFragment>videoCompression</InlineCodeFragment> are now set to <InlineCodeFragment>false</InlineCodeFragment> by default. Recording and compressing videos can be resource intensive, often impacting the duration of tests running in CI. Test Replay now serves as the primary replacement for debugging via video. We’ve changed these video options to be opt-in so you can configure recording video based on your needs.
              </p>

              <p>
                The <InlineCodeFragment>shouldUploadVideoOnPass</InlineCodeFragment> option is no longer available. This option was mostly used to skip video compression for unused videos which is now skipped by default. If you want to control which videos are saved locally or uploaded to Cypress Cloud, see our <ExternalLink href="https://on.cypress.io/migration-guide?utm_source=Binary%3A+App&utm_medium=splash-page&utm_campaign=v13#13-0-0">
                  documentation
                </ExternalLink> for our recommended workaround.
              </p>
            </div>
          </div>
          <hr class="border-gray-100">
          <div
            class="px-[16px] pt-[12px]"
            data-cy="previous-release-highlights"
          >
            <h2 class="font-bold mt-[24px] mb-[12px] text-[14px] text-gray-600">
              Previous release highlights
            </h2>
            <div class="pb-[8px]">
              <ExternalLink
                href="https://on.cypress.io/changelog#12-0-0"
                class="font-bold text-indigo-500"
              >
                12.0.0
              </ExternalLink>
              <span class="font-light pl-[10px] text-gray-500 text-[14px]">
                Released {{ versionReleaseDates['12'] }}
              </span>
            </div>
            <p class="text-[14px] leading-[20px]">
              We made <ExternalLink href="https://on.cypress.io/origin">
                <InlineCodeFragment>cy.origin()</InlineCodeFragment>
              </ExternalLink>, <ExternalLink href="https://on.cypress.io/session">
                <InlineCodeFragment>cy.session()</InlineCodeFragment>
              </ExternalLink>, and test isolation generally available to allow users to test multiple origin workflows while allowing users to rehydrate test state in a consistent manner.
              <br>
              <br>
              Read about the v12.0.0 changes in our
              <ExternalLink href="https://on.cypress.io/cypress-12-release">
                <!--eslint-disable-next-line vue/multiline-html-element-content-newline-->
                blog post</ExternalLink>.
            </p>
            <br>
            <div class="pb-[8px]">
              <ExternalLink
                href="https://on.cypress.io/changelog#11-0-0"
                class="font-bold text-indigo-500"
              >
                11.0.0
              </ExternalLink>
              <span class="font-light pl-[10px] text-gray-500 text-[14px]">
                Released {{ versionReleaseDates['11'] }}
              </span>
            </div>
            <p class="text-[14px] leading-[20px]">
              We made Component Testing generally available for projects using React, Next.js, Angular, and Vue which allows you to test your application's components without running your whole app! We also massively improved our startup performance with up to 84% faster startup times!
              <br>
              <br>
              Read about the v11.0.0 changes in our
              <ExternalLink href="https://on.cypress.io/cypress-11-release">
                <!--eslint-disable-next-line vue/multiline-html-element-content-newline-->
                blog post</ExternalLink>.
            </p>
            <br>
            <div class="pb-[8px]">
              <ExternalLink
                href="https://on.cypress.io/changelog#10-0-0"
                class="font-bold text-indigo-500"
              >
                10.0.0
              </ExternalLink>
              <span class="font-light pl-[10px] text-gray-500 text-[14px]">
                Released {{ versionReleaseDates['10'] }}
              </span>
            </div>
            <p class="text-[14px] leading-[20px]">
              We've reworked the Cypress app from the ground up to modernize the interface, streamline workflows and integrate better into your overall development experience.
              <br>
              <br>
              Read about breaking changes in our

              <ExternalLink href="https://on.cypress.io/cypress-10-release">
                <!--eslint-disable-next-line vue/multiline-html-element-content-newline-->
                blog post</ExternalLink>.
            </p>
          </div>
        </div>
      </div>

      <div
        class="bg-white flex border-t border-gray-100 w-full p-[16px] right-0 bottom-0 left-0 justify-between items-center absolute"
        :class="{'bottom-bar-box-shadow': shouldShowShadow}"
        data-cy="major-version-welcome-footer"
      >
        <Button
          class="group"
          size="lg"
          @click="handleClick"
        >
          {{ t('majorVersionWelcome.actionContinue') }}
          <template #suffix>
            <i-cy-chevron-right_x16 class="icon-dark-white" />
          </template>
        </Button>
        <ExternalLink
          href="https://on.cypress.io/changelog"
        >
          {{ t('majorVersionWelcome.linkReleaseNotes') }}
        </ExternalLink>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
import Button from '@cy/components/Button.vue'
import { useI18n } from '@cy/i18n'
import ExternalLink from '@packages/frontend-shared/src/gql-components/ExternalLink.vue'
import InlineCodeFragment from '@cy/components/InlineCodeFragment.vue'
import { useScroll, useElementSize, useTimeAgo } from '@vueuse/core'
import { computed, ref, useSlots } from 'vue'

const { t } = useI18n()

const scroller = ref<HTMLElement | null>(null)
const wrapper = ref<HTMLElement | null>(null)
const { arrivedState, y: scrollerY } = useScroll(scroller)
const { height: wrapperHeight } = useElementSize(wrapper)
const slots = useSlots()

const emit = defineEmits<{
  (eventName: 'clearLandingPage', value: void): void
}>()

const handleClick = () => {
  emit('clearLandingPage')
}

const versionReleaseDates = computed(() => {
  return {
    // Note, months are zero indexed.
    '10': useTimeAgo(Date.UTC(2022, 5, 1)).value,
    '11': useTimeAgo(Date.UTC(2022, 10, 8)).value,
    '12': useTimeAgo(Date.UTC(2022, 11, 6)).value,
    '13': useTimeAgo(Date.UTC(2023, 7, 30)).value,
  }
})

const shouldShowShadow = computed(() => {
  if (!scroller.value) {
    return false
  }

  const isScrolledToBottom = arrivedState.bottom

  const isTallEnoughToScroll = wrapperHeight.value < scroller.value.scrollHeight

  const showBecauseNotScrolledToBottom = isTallEnoughToScroll && !isScrolledToBottom
  const showBecauseHaveNotScrolledYet = isTallEnoughToScroll && scrollerY.value === 0

  return showBecauseNotScrolledToBottom || showBecauseHaveNotScrolledYet
})

</script>

<style scoped lang="scss">
.lp-wrapper {
  background-image: url("../images/Background.svg");
}

.bottom-bar-box-shadow {
  box-shadow: 0 -7px 11px -10px rgb(0 0 0 / 26%)
}
</style>
