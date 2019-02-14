<template>
    <div class="container">  
  <form id="contact" action="" method="post">    
    <fieldset>
      <input placeholder="firstname" type="text" tabindex="1" required autofocus>
    </fieldset>
    
    <fieldset>
      <input placeholder="lastname" type="text" tabindex="1" required autofocus>
    </fieldset>
    
    <fieldset>
      <input placeholder="Your Email Address" type="email" tabindex="2" required>
    </fieldset>
    
    <fieldset>
      <input placeholder="login" type="tel" tabindex="3" required>
    </fieldset>
    
    <fieldset>
      <input placeholder="mot de passe " type="tel" tabindex="3" required>
    </fieldset>
    
    <select class= "yes" name="titre">

    <option value="ville" selected="selected">Ville</option>
    <option value=">Paris">Paris</option>
    <option value="Marseille">Marseille</option>
    <option value="Lyon">Lyon</option>

    </select>
    <!--<fieldset>
      <input placeholder="City" type="url" tabindex="4" required>
    </fieldset>*-->
    
    <select class= "yes" name="titre">

    <option value="entité" selected="selected">Entité</option>
    <option value=">Paris">Buisness</option>
    <option value="Marseille">Sogety</option>

    </select>    
    <!--<fieldset>
      <textarea placeholder="Type your message here...." tabindex="5" required></textarea>
    </fieldset>-->
    
    <fieldset>
      <button name="submit" type="submit" id="contact-submit" data-submit="...Sending">Submit</button>
    </fieldset>
    <!--<p class="copyright">Designed by <a href="https://colorlib.com" target="_blank" title="Colorlib">Colorlib</a></p>-->
  </form>
</div>
</template>


<script>
export default {
  computed: {

  data() {
  },
  },
  methods: {
    displayMessage(msg, status) {
      if (!msg) return console.error(`the message is required !`);
      const possibleStatuses = ["success", "warning", "error"];
      if (possibleStatuses.includes(status)) {
        this.msgCls = status;
        this.msg = msg;
      } else console.warning(`${status} is not a valid css class for messages`);
    },
    createSalaried() {
      // this.user.id = Date.now();
      // this.$store.commit("addUser", this.user);
      this.$store.dispatch("addSalaried", this.salaried)
      .then(res => {
        this.displayMessage("new salaried has been created", "success");
      })
      .catch(res => {
        this.displayMessage("error during salaried creation", "error");
      })
    },
    handleSubmit(e) {
      e.preventDefault();
      if (!this.user.name || !this.user.lastname) {
        return this.displayMessage("Sorry, name AND lastname are required", "warning");
      }
      if (this.$route.params.id) this.updateUser();
      else this.createUser();
    }
  },
  props: ["title"]
};
</script>
