<template>
  <div class="t-member-template">
    <div class="t-member-template__sidebar">
      <SidebarMenu
        v-for="(item, index) in sidebar"
        :title="item.title"
        :menu="item.menu"
        :key="index"
      />
      <SidebarUser
        :username="$store.state.user.username"
      />
      <SidebarNavigation/>
    </div>
    <div class="t-member-template__content">
      <ACard class="t-member-template__card">
        <slot></slot>
      </ACard>
    </div>
  </div>
</template>

<script>
import ACard from '@/components/atoms/ACard';

import SidebarMenu from '@/components/organisms/sidebar/SidebarMenu';
import SidebarUser from '@/components/organisms/sidebar/SidebarUser';
import SidebarNavigation from '@/components/organisms/sidebar/SidebarNavigation';

export default {
  name: 'MemberTemplate',
  components: {
    ACard,
    SidebarMenu,
    SidebarUser,
    SidebarNavigation,
  },
  props: {
    sidebar: {
      type: Array,
      default: () => ([]),
    },
  },
};
</script>

<style lang="scss">
.t-member-template {
  padding-top: 30px;
  display: flex;
  flex-direction: column;
  &__sidebar {
    width: 100%;
    padding: 0 7.5px;
  }
  &__content {
    width: 100%;
    padding: 0 7.5px;
  }
  &__card {
    width: 100%;
    padding: 20px;
  }
  @media (min-width: $sm) {
    padding-top: 30px;
    display: flex;
    flex-direction: row;
    &__sidebar {
      padding: 0 7.5px;
      width: 33%;
      max-width: 300px;
    }
    &__content {
      width: 67%;
      padding: 0 7.5px;
    }
    &__card {
      padding: 20px;
    }
  }
}
</style>
