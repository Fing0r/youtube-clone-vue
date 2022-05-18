<template>
  <SidebarSection>
    <ul>
      <SidebarNavItem label="Home" icon-name="home" is-active/>
      <SidebarNavItem label="Trending" icon-name="trending"/>
      <SidebarNavItem label="Subscriptions" icon-name="subscriptions"/>
    </ul>
  </SidebarSection>
  <SidebarSection>
    <ul>
      <SidebarNavItem label="Library" icon-name="library"/>
      <SidebarNavItem label="History" icon-name="history"/>
    </ul>
  </SidebarSection>
  <SidebarSection class="px-8 py-4 font-medium leading-5 border-b">
      <span class="text-sm">
        Sign in to like videos, comment, and subscribe.
      </span>
    <ButtonLogin class="mt-3 px-2 py-0.5"/>
  </SidebarSection>
  <SidebarSection>
    <SidebarSectionHeading title="Best of YouTube"/>
    <ul>
      <SidebarNavItem label="Music" icon-name="music"/>
      <SidebarNavItem label="Sports" icon-name="sports"/>
      <SidebarNavItem label="Gaming" icon-name="gaming"/>
      <SidebarNavItem label="Movies" icon-name="movies"/>
      <SidebarNavItem label="News" icon-name="news"/>
      <SidebarNavItem label="Live" icon-name="live"/>
      <SidebarNavItem label="360&deg; Video" icon-name="aroundVideo"/>
    </ul>
  </SidebarSection>
  <SidebarSection>
    <ul>
      <SidebarNavItem label="Browse channels" icon-name="browChannels"/>
    </ul>
  </SidebarSection>
  <SidebarSection>
    <SidebarSectionHeading title="More from YouTube"/>
    <ul>
      <SidebarNavItem label="YouTube Premium" icon-name="premium"/>
      <SidebarNavItem label="Live" icon-name="live"/>
    </ul>
  </SidebarSection>
  <SidebarSection>
    <ul>
      <SidebarNavItem label="Settings" icon-name="settings"/>
      <SidebarNavItem label="Report history" icon-name="report"/>
      <SidebarNavItem label="Help" icon-name="help"/>
      <SidebarNavItem label="Send feedback" icon-name="sendFeedback"/>
    </ul>
  </SidebarSection>
  <SidebarSection class="px-6 py-4 text-xs font-semibold space-y-4">
    <TheFooter/>
  </SidebarSection>
</template>

<script>
import ButtonLogin from "./ButtonLogin.vue";
import SidebarNavItem from "./SidebarNavItem.vue";
import SidebarSectionHeading from "./SidebarSectionHeading.vue";
import SidebarSection from "./SidebarSection.vue";
import TheFooter from "./TheFooter.vue";

export default {
  name: "SidebarContent",
  components: {
    SidebarSection,
    SidebarNavItem,
    ButtonLogin,
    SidebarSectionHeading,
    TheFooter,
  },
}
</script>

<style scoped>

</style>
