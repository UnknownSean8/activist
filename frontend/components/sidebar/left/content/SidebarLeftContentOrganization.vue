<!-- SPDX-License-Identifier: AGPL-3.0-or-later -->
<template>
  <div class="flex flex-col items-center">
    <div
      class="relative"
      :class="{
        'h-32 w-32':
          sidebar.collapsed == false || sidebar.collapsedSwitch == false,
        'h-10 w-10':
          sidebar.collapsed == true && sidebar.collapsedSwitch == true,
      }"
    >
      <ImageOrganization
        class="elem-shadow-sm"
        :imgUrl="logoUrl"
        :alt="
          $t('i18n._global.entity_logo', {
            entity_name: name,
          })
        "
      />
      <!-- Change this button to use a button component not make one here. -->
      <button
        v-if="
          showButton &&
          (sidebar.collapsed == false || sidebar.collapsedSwitch == false)
        "
        @click="
          openModalUploadImages({
            fileUploadEntity: FileUploadEntity.ORGANIZATION_ICON,
          })
        "
        class="focus-brand absolute bottom-1 right-1 z-10 flex rounded-md border border-black/80 bg-white/80 p-1 text-black/80 dark:border-white/80 dark:bg-black/80 dark:text-white/80"
        ariaLabel="i18n.components.sidebar_left_content_organization.edit_aria_label"
      >
        <Icon :name="IconMap.EDIT" size="1em" />
      </button>
    </div>
    <ul
      id="submenu"
      class="mb-1 flex w-full flex-col px-1"
      :class="{
        'mt-4': sidebar.collapsed == false || sidebar.collapsedSwitch == false,
        'mt-2': sidebar.collapsed == true && sidebar.collapsedSwitch == true,
      }"
    >
      <li v-for="menuEntry in menuEntriesState.organizationEntry.value">
        <SidebarLeftSelector
          :id="'org-' + menuEntry.label.split('.').pop()"
          :label="menuEntry.label"
          :routeUrl="menuEntry.routeUrl"
          :iconUrl="menuEntry.iconUrl"
          :selected="menuEntry.selected"
        />
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import { FileUploadEntity } from "~/types/content/file-upload-entity";
import { IconMap } from "~/types/icon-map";

const props = defineProps<{
  name: string;
  logoUrl?: string;
}>();

const logoUrl = ref(props.logoUrl);

const sidebar = useSidebar();
const menuEntriesState = useMenuEntriesState();
const { openModal: openModalUploadImages } =
  useModalHandlers("ModalUploadImages");

const showButton = true;
</script>
