<script setup lang="ts">
import { definePageMeta, useAuth } from '#imports'
// Remember to disable the middleware protection from your page!
definePageMeta({
  auth: { unauthenticatedOnly: true, navigateAuthenticatedTo: '/' },
})

const { signIn, signOut, status } = useAuth()
console.log(status.value)
/*
 * NOTE: Here we hard-coded username and password
 * On your own page this should probably be connected to two inputs
 */
const demoCredentials = { username: 'test', password: 'hunter2' }
</script>

<template>
  <div>
    <p>Sign-In Options:</p>
    <Button @click="signIn('github')">
      Github
    </Button>
    <Button @click="signIn('credentials', demoCredentials)">
      Username and Password
    </Button>
    <Button variant="secondary" @click="signOut()">
      Sign Out
    </Button>
  </div>
</template>
