<template>
  <div class="userCard">
    <div class="userCard-top">
      <UserCardPicture :fruit="pfpFruit" />
      <div class="userCard-top-details">
        <div class="userCard-top-details-name">
          <span>{{ name }}</span>
        </div>
        <div class="userCard-top-details-age">
          <span>Age: {{ age }}</span>
        </div>
        <div class="userCard-top-details-phone">
          <span>Phone: {{ phone }}</span>
        </div>
        <div class="userCard-top-details-email">
          <span>Email: {{ email }}</span>
        </div>
      </div>
    </div>
    <div class="userCard-bottom">
      <div class="userCard-bottom-description">
        {{ description }}
      </div>
    </div>
  </div>
</template>

<script>
import UserCardPicture from './UserCardPicture';

export default {
  name: 'UserCard',
  components: {
    UserCardPicture,
  },
  props: {
    user: {
      type: Object,
      required: true,
    },
  },
  computed: {
    pfpFruit() {
      return this.user?.pfp || 'unknown';
    },
    name() {
      return this.user?.name || '';
    },
    age() {
      const age = this.user?.age || 0;
      return (age < 18) ? 'Minor' : age;
    },
    phone() {
      return this.user?.phone || 'N/A';
    },
    email() {
      return this.user?.email || 'N/A';
    },
    description() {
      return this.user?.description || 'Nothing here!';
    },
  },
};
</script>

<style lang='scss' scoped>
.userCard {
  background-color: white;
  border-radius: 10px;
  border: 3px solid cyan;
  display: flex;
  flex-flow: column nowrap;
  flex: 0 1 auto;
  margin: 20px;
  max-height: 200px;
  width: 22vw;

  &-top {
    display: flex;
    flex-flow: row nowrap;
    padding: 10px 10px 0 10px;

    &-details {
      flex: 1 0 auto;
      text-align: right;
    }
  }

  &-bottom {
    padding: 0px 10px 10px 10px;

    &-description {
      text-align: left;
    }
  }
}
</style>
