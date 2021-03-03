<template>
  <header class="bg-white py-5 shadow">
    <div class="container">
      <div class="flex items-center justify-between flex-wrap">
        <div class="flex items-center flex-no-shrink mr-4">
          <router-link
            :to="{ name: 'HomePage' }"
            class="text-black hover:text-grey-darkest no-underline font-semibold text-lg">
            Rooms
          </router-link>
        </div>
        <div class="flex items-center w-auto">
          <current-user>
            <template slot-scope="{ user }">
              <div class="items__controls">
                <div class="flex" v-if="user">
                  <router-link
                    :to="{ name: 'CreateHousePage' }"
                    class="no-underline mr-2 flex items-center text-grey-darkest">
                    <i class="material-icons">add</i>
                  </router-link>
                  <button class="mr-4 flex items-center">
                    <i class="material-icons">notifications</i>
                  </button>
                  <div class="flex items-center mr-4">
                    <img class="w-8 h-8 rounded-full mr-2"
                    src="https://i.pinimg.com/474x/7d/43/f2/7d43f284761ae9a89bdc380a0a4b4a52.jpg" alt="Avatar of Matthew Rosell">
                    <div class="text-sm">
                      <p class="text-black leading-none">{{ user.name }}</p>
                      <p class="text-grey-dark">Online</p>
                    </div>
                  </div>
                  <button class="flex items-center" @click.prevent="logOut">
                    <i class="material-icons">exit_to_app</i>
                  </button>
                </div>
                <div v-else>
                  <button class="btn__outline btn__outline--teal rounded mr-2"
                   @click.prevent="getLogin">Login</button>
                  <button
                    @click.prevent="signUp"
                    class="bg-yellow-dark text-yellow-darker font-semibold py-2 px-4 rounded">
                    Register</button>
                </div>
              </div>
            </template>
          </current-user>
        </div>
      </div>
    </div>
  </header>
</template>

<script>
import CurrentUser from '@/components/CurrentUser.vue';

export default {

  name: 'HeaderPartial',

  methods: {
    getLogin() {
      this.$store.dispatch('TOGGLE_MODAL_STATE', {
        name: 'login',
        value: true,
      });
    },
    signUp() {
      this.$store.dispatch('TOGGLE_MODAL_STATE', {
        name: 'register',
        value: true,
      });
    },
    logOut() {
      this.$store.dispatch('LOG_OUT');
    },
  },
  components: {
    CurrentUser,
  },
};
</script>
