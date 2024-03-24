<template>
  <div>
    <div class="letter-title">You are invited!</div>
    <p class="letter-description">We reserved seats for you and your family. <br>Please confirm your attendance below.</p>
    <p style="margin:50px 0px 0 0px;text-align:center;">
      <a href="https://form.jotform.com/240833295186462" title="RSVP" target="_blank" style="display:inline;">
        <img src="https://buttons.addevent.com/rsvp-813b0a-r48-icotxt-s40.png" alt="RSVP" height="40" border="0" style="height:40px;display:inline;" />
      </a>
    </p>
  </div>
</template>

<script setup>
const attendance = ref(null)

const setAttendance = (willAttend) => {
  attendance.value = willAttend === true;
}
</script>

<style></style>