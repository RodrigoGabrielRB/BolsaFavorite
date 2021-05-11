<template>
  <div class="modal" v-show="isModalAddCourseOpen">
      <div class="modal__x"><i class="fas fa-times"></i></div>
      <div class="modal__content">
        <div class="modal__content__title">
            <h2>Adiconar Bolsa</h2>
            <p>Filtre e adicione as bolsas de seu interesse.</p>
            {{filter}}
        </div>
        <div class="modal__content__filter">
            <p>Selecione sua cidade</p>
            <select v-model="filter.city" @change="changeCity">
                <option v-for="(city, index) in allCities" :key="index">{{city}}</option>
            </select>
        </div>
        <div class="modal__content__filter">
            <p>Selecione o curso de sua preferência</p>
            <select v-model="filter.course">
                <option v-for="(city, index) in allCourseFilteredByCity" :key="index">{{city}}</option>
            </select>
        </div>
        <div class="modal__content__filter">
            <input type="checkbox" v-model="filter.presencial"> Presencial
            <input type="checkbox" v-model="filter.ead"> A distância
        </div>
        <div class="modal__content__filter">
            Até quando pode pagar?
            R${{filter.moneyToPaid}}
            <input type="range" v-model="filter.moneyToPaid" min="1" max="10000">
        </div>
        <div class="modal__content__filter">
            <div>Resultado:</div>
            <div>Ordernar Por: 
                <select>
                    <option>Nome da Faculdade</option>
                    <option>Pokemon</option>
                </select>
            </div>
        </div>
        {{teste}}
        <div class="modal__content__list">
           <div class="modal__content__list__item" v-for="(course, index) in allCourse" :key="index">
               <div class="modal__content__list__item__checkbox">
                   <input type="checkbox" :value="course">
               </div>
               <div class="modal__content__list__item__img">
                   <img :src="course.university.logo_url">
               </div>
               <div class="modal__content__list__item__text">
                   <p>{{course.course.name}}</p>
                   <p>{{course.course.level}}</p>
                   <p>Bolsa de <span>{{course.discount_percentage}}%</span></p>
                   <p>R$ {{course.price_with_discount}}/mês</p>
               </div>
           </div>
        </div>
      </div>
  </div>
</template>

<script>

import { telaService } from '../services'

export default {
    name: "Modal",
    props: [
        'isModalAddCourseOpen'
    ],
    data: () => ({
        teste: null,
        allCourse: null,
        filter: {
            city: null,
            course: null,
            presencial: false,
            ead: false,
            moneyToPaid: 10000,
        },
        
        allCities: null,
        allCourseFilteredByCity: null,
    }),
    methods: {
        getAllCities(){
            
            const allCities = this.allCourse.map(item => item.campus.city);

            this.allCities = allCities.filter((item, pos) => {
                                return allCities.indexOf(item) == pos;
                            })  
        },
        changeCity(){
            this.getAllCourseByCity(this.filter.city);
        },
        getAllCourseByCity(city){
            const allCourse = this.allCourse.filter(item => item.campus.city == city);

            const allOptionCourse = allCourse.map(item => item.course.name) 

            this.allCourseFilteredByCity = allOptionCourse.filter((item, pos) => {
                                return allOptionCourse.indexOf(item) == pos;
                            })  

            // this.allCourseFilteredByCity = 
        }
    },
    async mounted(){
        try{
            this.allCourse = await telaService.getAllCourse();
        }catch(error){
            console.log(error)
        }finally{
            console.log("reset login");
        }

        this.getAllCities();
    }
}
</script>

<style lang="scss" scoped>
    .modal{
        background-color:rgba(31,45,48,0.88);
        z-index: 1;
        position: absolute;
        top: 0;
        left:0;
        width: 100%;
        height: 100vh;
        &__x{
            color:white;
            text-align: right;
            padding: 10px 20px 10px 0;
            font-size:2em;
        }
        &__content{
            width: 100%;
            padding: 20px;
            background-color: white;
            opacity:1;
        }
    }

</style>