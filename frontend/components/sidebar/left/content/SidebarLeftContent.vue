<!-- SPDX-License-Identifier: AGPL-3.0-or-later -->
<template>
  <div
    class="elem-shadow-sm mx-1 rounded-md bg-layer-2 pb-1 pt-2 transition-all duration-500"
  >
    <SidebarLeftContentOrganization
      v-if="sidebarTypeToDisplay === SidebarType.ORGANIZATION_PAGE"
      :logo-url="logoUrl"
      :name="props.name"
    />
    <SidebarLeftContentEvent
      v-else-if="sidebarTypeToDisplay === SidebarType.EVENT_PAGE"
      :logo-url="logoUrl"
      :name="props.name"
    />
    <SidebarLeftContentGroupPage
      v-else-if="sidebarTypeToDisplay === SidebarType.GROUP_PAGE"
      :logo-url="logoUrl"
      :name="props.name"
    />
  </div>
</template>

<script setup lang="ts">
import { SidebarType } from "~/types/sidebar-type";

const props = defineProps<{
  name: string;
  sidebarType:
    | SidebarType.ORGANIZATION_PAGE
    | SidebarType.EVENT_PAGE
    | SidebarType.GROUP_PAGE;
  logoUrl?: string;
}>();
const logoUrl = ref(props.logoUrl);

const sidebarTypeToDisplay = computed(() => props.sidebarType);
</script>
