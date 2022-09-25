<template>
  <div class="sidebar" :class="{active: isSidebarActive}">
    <div class="list">
      <li v-on="{mouseover: handleMouseOver, mouseleave: handleMouseLeave}" ref="l-1" class="list__item" id="list__item-1">
        <span class="icon"><ion-icon name="home-outline"></ion-icon></span>
        <span class="list__title">Home</span>
      </li>
      <li v-on="{mouseover: handleMouseOver, mouseleave: handleMouseLeave}" ref="l-2" class="list__item" id="list__item-2">
        <span class="icon"><ion-icon name="person-outline"></ion-icon></span>
        <span class="list__title">Profile</span>
      </li>
      <li v-on="{mouseover: handleMouseOver, mouseleave: handleMouseLeave}" ref="l-3" class="list__item" id="list__item-3">
        <span class="icon"><ion-icon name="chatbubble-ellipses-outline"></ion-icon></span>
        <span class="list__title">Messages</span>
      </li>
      <li v-on="{mouseover: handleMouseOver, mouseleave: handleMouseLeave}" ref="l-4" class="list__item" id="list__item-4">
        <span class="icon"><ion-icon name="settings-outline"></ion-icon></span>
        <span class="list__title">Settings</span>
      </li>
      <li v-on="{mouseover: handleMouseOver, mouseleave: handleMouseLeave}" ref="l-5" class="list__item" id="list__item-5">
        <span class="icon"><ion-icon name="help-circle-outline"></ion-icon></span>
        <span class="list__title">Help</span>
      </li>
      <li v-on="{mouseover: handleMouseOver, mouseleave: handleMouseLeave}" ref="l-6" class="list__item" id="list__item-6">
        <span class="icon"><ion-icon name="log-out-outline"></ion-icon></span>
        <span class="list__title">Signout</span>
      </li>
    </div>
  </div>
  <div class="toggle" @click="handleToggleClick">
    <ion-icon name="menu-outline" id="menu" v-show="isToggleActive"></ion-icon>
    <ion-icon name="close-outline" id="close" v-show="!isToggleActive"></ion-icon>
  </div>
</template>

<script>
export default {
  name: "Sidebar",
  data() {
    return {
      doesHaveId: false,
      isSidebarActive: false,
      isToggleActive: true,
    }
  },
  methods: {
    handleMouseOver(e) {
      let id = e.path.filter(el=> el.id?.includes('list'))[0].id.at(-1);
      let refs= Object.values(this.$refs)
      refs.forEach(r=>  {
        if(r.id.includes(id))
        r.classList.add('active')
        else
        r.classList.remove('active');
      });
    },
    handleMouseLeave() {
      let refs= Object.values(this.$refs);
      refs.forEach(r=> r.classList.remove('active'));
    },
    handleToggleClick(e) {
      this.isToggleActive = !this.isToggleActive;
      this.isSidebarActive = !this.isSidebarActive;
    }
  }
};
</script>

<style scoped>
  .sidebar {
    width: 60px;
    height: 100vh;
    background: #561467;
    overflow-x: hidden;

    transition: width .4s ease;
  }

  .sidebar.active {
    width: 250px;
  }


  .list {
    width: 100%;
    transform: translateY(20%);
  }

  .list__item {
    list-style: none;
    color: #F1BBFF;
    font-size: 22px;
    display: flex;
    align-items: center;
    gap: 20px;
    line-height: 40px;
    width: 100%;
    transition: all .4s ease;
    text-align: center;
    border-top-left-radius: 10px;
    border-bottom-left-radius: 10px;
    cursor: pointer;
    padding: 5px;

    margin-left: 15px;
    margin-bottom: 20px;
  }

  .list__item:hover {
    background: #fff;
    color: #000;
  }

  .active {
    color:red;
  }

  .toggle {
    position: fixed;
    top: 20px;
    right: 20px;
    background: #561467;
    padding: 10px;
    font-size: 20px;
    color: #F1BBFF;
    border-radius: 5px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
  }

  .icon {
    display: flex;
    align-items: center;
    justify-content: center;
  }

/*
  .sidebar .list > .list__item > .list__title {
    display: none;
    transition: display .4s ease;
  }
  .sidebar.active .list > .list__item > .list__title {
    display: block;
  }
*/


</style>
