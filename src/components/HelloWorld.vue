<template>
  

  <div   class="titulo col-12" style="margin-top:10px">
    <h1>Templo de Brasília - Visitação</h1>
  </div>

  


<div class="row col-12">
  <div class="col-4">
    <h2>
      Como Agendar:
    </h2>
    <v-card-text> 
          <v-textarea
            counter
            label="Observação:"
            :rules="rules"
            :value="value"
          ></v-textarea>
        </v-card-text>  
  </div>
 
  <div  class="col-8">
    <FullCalendar :options="calendarOptions" />
  </div>
</div>

<v-dialog
      v-model="dialogCreateEvent"
      max-width="525">
      <v-card v-if="dialogCreateEvent">
        <v-card-title class="headline">{{ createEventDate.toLocaleDateString() }} - Preencha o formulário</v-card-title>
        <v-card-text>
          <v-text-field
            v-model="newEventTitle"
            label="Nome"
            hint="Nome" />
       
          <v-text-field
            v-model="newEventTitle"
            label="Hora"
            hint="Hora" />
          
            <v-text-field
            v-model="newEventTitle"
            label="Qtd Pessoas"
            hint="qtdPes" />
        </v-card-text>

        <v-card-text>
          Idioma <br>
          <v-radio-group v-model="selectedEventClass" row>
            <v-radio
              label="Portugues"
              color="blue"
              value="pt"/>
            <v-radio
              label="Inglês"
              color="red"
              value="en"/>
            <v-radio
              label="Espanhol"
              color="green"
              value="es"/>
            <v-radio
              label="Francês"
              color="yellow"
              value="fr"/>
          </v-radio-group>
        <!-- </v-card-text>
        <v-card-text> -->
          Necessidades Especiais <br>
          <v-radio-group v-model="selectedEventClass" row>
            <v-radio
              label="Sim"
              color="blue"
              value="S"/>
            <v-radio
              label="Não"
              color="red"
              value="N"/>
          </v-radio-group>
        <!-- </v-card-text>

        <v-card-text> -->
          <v-textarea
            counter
            label="Observação:"
            :rules="rules"
            :value="value"
          ></v-textarea>
        </v-card-text>  
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="green darken-1"
            flat="flat"
            @click="dialogCreateEvent = false">
            Cancelar
          </v-btn>
          <v-btn
            color="green darken-1"
            flat="flat"
            @click="createEvent()">
            Submeter
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>








</template>
<script>
import '@fullcalendar/core/vdom' // solves problem with Vite
import FullCalendar from '@fullcalendar/vue3'
import dayGridPlugin from '@fullcalendar/daygrid'
import timeGridPlugin from "@fullcalendar/timegrid"
import interactionPlugin from '@fullcalendar/interaction'


// Vuetify
import 'vuetify/styles'
import { createVuetify } from 'vuetify'
import * as components from 'vuetify/components'
import * as directives from 'vuetify/directives'

const vuetify = createVuetify({
  components,
  directives,
})

createApp(App).use(vuetify).mount('#app')

// import allLocales from '@fullcalendar/core/locales-all';


// import {
//   CalendarOptions,
//   EventApi,
//   DateSelectArg,
//   EventClickArg,
// } from "@fullcalendar/vue3";

// let calendar = new Calendar(calendarEl, {
//   locales: allLocales,
//   locale: 'pt-br' // the initial locale
// });

// calendar.setOption('locale', 'pt-br');

export default {
  name: "HelloWorld",
  

  components: { 
    FullCalendar // make the <FullCalendar> tag available
  },
  data() {
    return {

      dialog: false,
      dialogCreateEvent: false,
      newEventTitle: null,
      createEventDate: null,
      selectedEventClass: null,
      selectedEvent: null,
      events: [],




      calendarOptions: {
        plugins: [
            dayGridPlugin,
            timeGridPlugin,
            interactionPlugin, // needed for dateClick
          ],
        initialView: 'timeGridWeek',
        headerToolbar: {
          right: "prev,next",
          //center: "title",
          // right: "dayGridMonth,timeGridWeek,timeGridDay",
        },
        editable: true,
        selectable: true,
        selectMirror: true,
        dayMaxEvents: true,
        weekends: true,
        


        /* you can update a remote database when these fire:
        eventAdd:
        eventChange:
        eventRemove:
        */

      }
    }
  },






  props: {
    msg: String,
  },
  methods: {
    eventClick($event) {
      const vm = this;

      vm.dialog = true;

      vm.selectedEvent = $event;
    },

    dayClick($event) {
      const vm = this;

      vm.dialogCreateEvent = true;

      vm.createEventDate = $event;
    },

    createEvent() {
      const vm = this;

      vm.events.push({
        title: vm.newEventTitle ? vm.newEventTitle : 'Sample Event',
        start: vm.createEventDate,
        cssClass: vm.selectedEventClass ? vm.selectedEventClass : null
      });

      vm.createEventDate = null;
      vm.newEventTitle = '';
      vm.dialogCreateEvent = false;
    }
  }
}

</script>
<style scoped>

.titulo h1 {
  color: rgb(1, 11, 148);
  font-size: 44px;
  font-weight: bold;
  margin-bottom: 30px;

}

/* .hbg-nav {
  background-image: url("..\assets\bg_brasilia.png");
} */

</style>
