<template>

<nav class="navbar navbar ">
  <div class="container-fluid">
          <router-link :to="{ name: 'home' }" class="navbar-brand"><img src="../assets/logo.png" alt="logo" class="logo" ></router-link>

           <nav class="navbar navbar-expand-lg  ">
            <div class="container-fluid" > 
              
              <div class="collapse navbar-collapse justify-content-center " id="navbarSupportedContent">
                <ul class="navbar-nav  mb-2 mb-lg-0">
                       
                  
                  <!-- ----------desplegable Escuela Montaño-------- -->
                  <li class="nav-item dropdown " >
                    <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false" >
                      {{ $t("navbar.escuela") }}
                    </a>
                    <ul class="dropdown-menu">
                      <li >
                          <router-link :to="{ name: 'about' }" class="dropdown-item">{{ $t("navbar.somos") }}</router-link>
                      </li>
                      <li >
                          <a href="about#contacto" class="dropdown-item">{{ $t("navbar.contacto") }}</a>
                      </li>
                     
                    </ul>
                  </li>
                  
                  <li class="nav-item">
                    <router-link :to="{ name: 'menu-dia' }" class="nav-link">{{ $t("navbar.menu_dia") }}</router-link>
                  </li>
                  
                  <li class="nav-item">
                    <router-link :to="{ name: 'menu-estrella' }" class="nav-link">{{ $t("navbar.menu_estrella") }}</router-link>
                  </li>
                               
                  <!-- ----------desplegable Mas--------- -->
                  <li class="nav-item dropdown">
                    <a class="nav-link dropdown-toggle" href="#" role="button" data-bs-toggle="dropdown" aria-expanded="false">
                      {{ $t("navbar.mas") }}
                    </a>
                    <ul class="dropdown-menu">
                      <li>
                          <router-link :to="{ name: 'carniceria' }" class="dropdown-item">{{ $t("navbar.carniceria") }}</router-link>
                      </li>
                      <li>
                          <router-link :to="{ name: 'pasteleria' }" class="dropdown-item">{{ $t("navbar.pasteleria") }}</router-link>
                      </li>
                                            <li>
                            <router-link :to="{ name: 'raciones' }" class="dropdown-item">{{ $t("navbar.raciones") }}</router-link>
                        </li>
                        <li>
                            <router-link :to="{ name: 'pintxos' }" class="dropdown-item">{{ $t("navbar.pinchos") }}</router-link>
                        </li>
                    </ul>
                  </li>


                  </ul> 

                  <ul>
                <!-- ----------desplegable idioma--------- -->
                    <li class="nav-item dropdown">

                        <i class="fa-solid fa-globe idioma-icono"></i>
                        <select v-model="$i18n.locale">
                          <option v-for=" locale in $i18n.availableLocales" :key="`locale-${locale}`" :value="locale">{{ locale }}</option>
                        </select>

                    </li>
                  </ul>
              </div>
            </div>
          </nav>     
        </div>   
      </nav>

</template>

<script setup>


</script> 

<style lang="scss" scoped>
.navbar-toggler {
    display: none;
}

.idioma-icono{
  font-size: 1rem;
  padding: 0.2rem;
}

.logo{
  width: 10vw;
  min-width: 100px;
}

.bandera-idioma{
  width: 1.5rem;
  margin-right: .2rem;
}

@media only screen and (max-width: 980px) {
  .logo{
  min-width: 100px;
}

.navbar-toggler {
        display: block;
    }
}


.nav-item .router-link-exact-active {
      color: #128652;
      font-weight: 500;
    }
</style>


    