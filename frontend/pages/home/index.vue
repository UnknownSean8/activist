<!-- SPDX-License-Identifier: AGPL-3.0-or-later -->
<template>
  <div id="home-page-main" class="bg-layer-0 px-4 pb-4 xl:px-8">
    <Head>
      <Title>{{ $t("i18n._global.home") }}</Title>
    </Head>
    <HeaderAppPage
      :header="$t('i18n.pages.home.index.header')"
      :tagline="$t('i18n.pages.home.index.subheader')"
    >
      <ComboboxTopics class="pb-3 lg:pb-4" />
    </HeaderAppPage>
    <!-- <div class="space-y-6 pb-6">
      <div
        class="flex flex-col space-y-6 lg:mr-6 lg:grid lg:grid-cols-7 lg:grid-rows-1 lg:space-x-6 lg:space-y-0"
      >
        <CardMetricsOverview
          class="lg:col-span-5"
          :metrics="{
            'total events': 123,
            'action events': 100,
            'learn events': 23,
            'new orgs': 10,
          }"
        />
        <MediaCalendar class="h-full w-full lg:col-span-2" />
      </div>
    </div> -->
  </div>
</template>
