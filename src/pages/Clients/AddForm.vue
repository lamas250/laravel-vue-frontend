<template>
    <div class="container">
        <form action="" class="form">
            <div class="form-row">
                <div class="col-12 col-md-4">
                    <input type="text" class="form-control"  name="name"
                        placeholder="Nome" 
                        @change="handleChange" 
                        :value="form.name"/>
                </div>
                <div class="col-12 col-md-4">
                    <input type="email" class="form-control"  name="email" 
                        placeholder="E-mail" 
                        @change="handleChange" 
                        :value="form.email"
                    />
                </div>
                <div class="col-12 col-md-2">
                    <input type="text" class="form-control" placeholder="Telefone"
                        name="phone"
                        @change="handleChange" 
                        :value="form.phone"/>
                </div>
                <div class="col-12 col-md-1" style="text-align: right;">
                    <button type="submit" :class="btnClass" @click="onFormSubmit" >{{ btnName }}</button>
                </div>
            </div>
        </form>        
    </div>
</template>

<script>
export default {
    name: 'AddClient',
    data() {
        return {
            btnName: "Salvar",
            btnClass: "btn btn-info btn-sm",
        };
    },
    props: {
        form: {
            type: Object
        }
    },
    methods: {
        handleChange(event){
          const { name, value } = event.target;
          let form = this.form;
          form[name] = value;
          this.form = form;
        },
        onFormSubmit(event) {
            event.preventDefault();

            if(this.formValidation()){
                //   console.log(this.form);
                this.$emit("onFormSubmit", this.form);

                // change the button to save
                this.btnName = "Salvar";
                this.btnClass = "btn btn-info btn-sm";

                this.clearFilds();
            }
        },
        formValidation(){
          if(document.getElementsByName('name')[0].value === ""){
              alert("Escreva um nome");
              return false;
          }
           if(document.getElementsByName('email')[0].value === ""){
              alert("Escreva um email");
              return false;
          }
           if(document.getElementsByName('phone')[0].value === ""){
              alert("Escreva um telefone");
              return false;
          }
          return true;
        },
        clearFilds(){
            //clear form data
            this.form.name = "";
            this.form.email = "";
            this.form.phone = "";
            this.form.isEdit = false;

            //clear form filds
            document.querySelector(".form").reset();
        },
        updated(){
            if(this.form.isEdit){
                console.log('teste');
                this.btnName = "Ediar",
                this.btnClass = "btn btn-warning btn-sm"
            }
        }
    },

}
</script>

<style>
.container {
    padding: 10px;
}

</style>