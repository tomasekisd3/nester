<template>
    <div>
        <v-card v-if="!sended" class="pa-10 mt-6 mx-2">
            <v-row>
                <v-col cols="12" class="d-flex text-h4 justify-start">
                    <div class="color-custom-default">Registro rápido</div>
                </v-col>
            </v-row>
            <!-- <v-row>
                <v-col cols="12" class="d-flex text-h4 justify-start">
                    {{ center }}
                </v-col>
            </v-row> -->
            <!-- <v-row>
                <v-col cols="12" class="text-h5 color-custom-default">
                    Fecha <v-icon class="pb-1" color="#47BCC2">mdi-calendar</v-icon>
                </v-col>
            </v-row> -->
            <v-row>
                <!-- <v-col cols="12" class="d-flex text-h5 justify-start" style="font-weight: 300;">
                    Registra el nido que estás viendo presionando el botón a continuación:
                </v-col> -->
                <v-col cols="12" class="d-flex text-h5 justify-start" style="font-weight: 400;">
                    <div>Completa la siguiente información:</div>
                    <!-- <div>
                        <v-btn icon @click="getLocation()" class="ml-3 pb-3">
                            <v-icon x-large class="ml-3 " color="#47BCC2">mdi-map-marker-plus-outline</v-icon>
                        </v-btn>
                    </div> -->
                </v-col>
            </v-row>
            <v-row>
                <v-col
                    sm="12"
                    md="6"
                    >
                    <v-menu
                        v-model="menu"
                        :close-on-content-click="false"
                        :nudge-right="40"
                        transition="scale-transition"
                        offset-y
                        min-width="auto"
                    >
                        <template v-slot:activator="{ on, attrs }">
                            <v-text-field
                                v-model="date"
                                label="Fecha"
                                dense
                                placeholder="Ingrese la fecha del avistamiento del nido"
                                persistent-placeholder
                                prepend-inner-icon="mdi-calendar"
                                readonly
                                outlined
                                v-bind="attrs"
                                v-on="on"
                            ></v-text-field>
                        </template>
                        <v-date-picker
                            v-model="date"
                            @input="menu2 = false"
                            ></v-date-picker>
                    </v-menu>
                </v-col>
                <v-col md="6" sm="12">
                    <v-menu
                        ref="menu"
                        v-model="menu2"
                        :close-on-content-click="false"
                        :nudge-right="40"
                        :return-value.sync="time"
                        transition="scale-transition"
                        offset-y
                        max-width="290px"
                        min-width="290px"
                    >
                        <template v-slot:activator="{ on, attrs }">
                            <v-text-field
                                v-model="time"
                                label="Hora"
                                dense
                                placeholder="Ingrese la hora del avistamiento del nido"
                                persistent-placeholder
                                prepend-inner-icon="mdi-clock-time-four-outline"
                                outlined
                                readonly
                                v-bind="attrs"
                                v-on="on"
                            ></v-text-field>
                        </template>
                        <v-time-picker
                            v-if="menu2"
                            v-model="time"
                            full-width
                            @click:minute="$refs.menu.save(time)"
                        ></v-time-picker>
                    </v-menu>
                </v-col>
                <!-- <v-col cols="12" class="d-flex text-h5 justify-start" style="font-weight: 300;">
                    <div>Registra la ubicación el nido que estás viendo:</div>
                    <div>
                        <v-btn icon @click="getLocation()" class="ml-3 pb-3">
                            <v-icon x-large class="ml-3 " color="#47BCC2">mdi-map-marker-plus-outline</v-icon>
                        </v-btn>
                    </div>
                </v-col> -->
            </v-row>
            <v-row v-if="false" class="mt-15">
                <v-col cols="12" class="text-h5 color-custom-default">
                    Ubicación <v-icon class="pb-2" color="#47BCC2">mdi-map-marker-plus-outline</v-icon>
                </v-col>
            </v-row>
            <v-row>
                <!-- <v-col cols="12" class="d-flex text-h5 justify-start" style="font-weight: 300;">
                    Registra el nido que estás viendo presionando el botón a continuación:
                </v-col> -->
                <v-col cols="12" class="d-flex text-h5 justify-start" style="font-weight: 400;">
                    <div>Registra la ubicación del nido:</div>
                </v-col>
                <v-col cols="12" class="d-flex text-h6 justify-start" style="font-weight: 300;">
                    <div>Para mayor exactitud quédate lo más cerca del árbol y apreta el botón a continuación</div>
                </v-col>
                <v-col cols="12">
                    <div>
                        <!-- <v-btn outlined dark @click="location2()" color="#47BCC2" class="ml-0">
                            Registrar -->
                        <v-btn dark elevation="0" @click="getLocation()" color="#47BCC2" class="ml-0">
                            Registrar
                            <v-icon dark class="ml-3">mdi-map-marker-plus-outline</v-icon>
                        </v-btn>
                    </div>
                </v-col>
            </v-row>
            <v-row>
                <!-- <v-col cols="12">
                    {{ `Latitud: ${latitude}, Longitud: ${longitude}` }}
                </v-col> -->
                <!-- <v-col cols="12">
                    <v-btn text @click="getLocation()">
                        <v-icon x-large class="ml-3" color="primary">mdi-map-marker-plus-outline</v-icon>
                    </v-btn>
                </v-col> -->
                <!-- <v-col cols="12">
                    <google-map id="map" ref="Map">
                        <google-map-marker
                            :key="index"
                            v-for="(infoWindow, index) in infoWindowsList"
                            :position="infoWindow.position"
                            @click="toggleInfoWindow(infoWindow)"
                        />
                        <google-map-infowindow
                            :position="infoWIndowContext.position"
                            :show.sync="showInfo"
                            :options="{maxWidth: 300}"
                            @info-window-clicked="infoClicked"
                        >
                            <h4>{{infoWindowContext.title}}</h4>
                            <p>{{infoWindowContext.description}}</p>
                        </google-map-infowindow>
                    </google-map>
                </v-col> -->
                <v-col cols="12" v-if="false">
                    <div>
                        <h2>Vue Js Search and Add Marker</h2>
                        <label>
                            <gmap-autocomplete @place_changed="initMarker"></gmap-autocomplete>
                            <button @click="addLocationMarker">Add</button>
                        </label>
                        <br/>
                
                    </div>
                </v-col>
                <v-expand-transition>
                    <!-- <v-col cols="12" v-if="buttonAction" style="max-width: 800px; border: 5px solid #47BCC2;"> -->
                    <v-col cols="12" v-if="buttonAction" style="max-width: 800px">
                        <v-card class="pa-1" color="#47BCC2">
                            <gmap-map
                                :zoom="18"    
                                :center="center"
                                style="width:100%;  height: 600px;"
                                :options="{
                                    zoomControl: true,
                                    mapTypeControl: false,
                                    scaleControl: false,
                                    streetViewControl: false,
                                    rotateControl: false,
                                    fullscreenControl: true,
                                    disableDefaultUi: false
                                }"
                            >
                            <gmap-marker
                                :key="index"
                                v-for="(m, index) in locationMarkers"
                                :position="m.position"
                                @click="center=m.position"
                            ></gmap-marker>
                            </gmap-map>
                        </v-card>
                    </v-col>
                </v-expand-transition>
            </v-row>
            
            <v-row class="mt-5">
                <v-col cols="12" class="d-flex text-h6 justify-start" style="font-weight: 400;">
                    <div>Añade una foto del nido: </div>
                </v-col>
                <v-col md="6" sm="12" class="text-h4">
                    <v-file-input
                        v-model="showImg"
                        accept="image/png, image/jpeg, image/bmp"
                        placeholder="Selecciona o toma una imagen"
                        persistent-placeholder
                        dense
                        prepend-icon=""
                        prepend-inner-icon="mdi-camera"
                        label="Imagen del árbol"
                        outlined
                    />
                </v-col>
            </v-row>
            <v-expand-transition>
                <v-row no-gutters v-if="showImg">
                    <div style="border: 2px solid #47BCC2; max-width: 500; max-height: 500; min-width: 300; min-height: 300;">
                        <v-img min-width="300" min-height="300" max-width="500" max-height="500" :src="imgUrlHandler()" />
                    </div>
                </v-row>
            </v-expand-transition>
            <v-row class="mt-10">
                <v-col cols="12" class="text-h5 color-custom-default">
                    <v-btn color="secondary" elevation="0" @click="cancelNest()">cancelar</v-btn>
                    <v-btn dark class="ml-5" color="#47BCC2" elevation="0" @click="registerNest()">guardar</v-btn>
                </v-col>
            </v-row>
        </v-card>
        <v-row v-if="sended" class="pa-10 mt-6 mx-2">
            <v-col cols="12" class="text-h4 secondary--text">
                El nido fue registrado exitosamente! <v-icon x-large color="success">mdi-check</v-icon>
            </v-col>
            <v-col cols="12" class="text-h4 secondary--text">
                <v-icon x-large color="#47BCC2">mdi-spin mdi-loading</v-icon>
            </v-col>
        </v-row>
        <v-layout row justify-center>
            <v-dialog v-model="showError" persistent max-width="290">
                <v-card>
                    <v-card-title class="headline">Permitir ubicación</v-card-title>
                    <v-card-text>Usted tiene bloqueados los permisos de ubicación, desbloquee el sitio o navegador en las configuraciones de su dispositivo para poder registrar las coordenadas del nido.</v-card-text>
                    <v-card-actions class="pb-5">
                        <v-spacer></v-spacer>
                        <v-btn dark color="#47BCC2" @click="showError = false">Cerrar</v-btn>
                    </v-card-actions>
                </v-card>
            </v-dialog>
        </v-layout>
    </div>
</template>

<script>
export default {
    name: 'CitizenRegister',
    data() {
        return {
            sended: false,
            showImg: null,
            time: null,
            menu2: false,
            latitude: '',
            longitude: '',
            // center: { 
            //     lat: 39.7837304,
            //     lng: -100.4458825
            // },  
            center: { 
                lat: 0,
                lng: 0
            },  
            showError: false,
            locationMarkers: [],
            locPlaces: [],
            existingPlace: null,
            buttonAction: false,
            date: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
            menu: false,
        }
    },
    mounted() { 
        // this.buttonAction = true
        this.startTime()
        // this.location2()
        this.getLocation()

    },
    methods: {
        location2() {
            navigator.geolocation.getCurrentPosition(position => {
                const { latitude, longitude } = position.coords;
                // Show a map centered at latitude / longitude.
                this.center.lat = latitude
                this.center.lng = longitude
                this.buttonAction = true

                const marker = {
                    lat: this.center.lat,
                    lng: this.center.lng
                };
                this.locationMarkers.push({ position: marker });
                this.locPlaces.push(this.existingPlace);
                this.center = marker;
                this.existingPlace = null;
            })
        },
        initMarker(loc) {
            this.existingPlace = loc;
        },
        addLocationMarker() {
            if (this.existingPlace) {
                const marker = {
                lat: this.existingPlace.geometry.location.lat(),
                lng: this.existingPlace.geometry.location.lng()
                };
                this.locationMarkers.push({ position: marker });
                this.locPlaces.push(this.existingPlace);
                this.center = marker;
                this.existingPlace = null;
            }
        },
        // getLocation() {
        //     console.log('esto es img: ', this.showImg)
        //     const success = (position) => {
        //         console.log('esto es position: ', position)
        //         console.log('esto es BOTON: ', this.time)
        //         this.center.lat = position.coords.latitude
        //         this.center.lng = position.coords.longitude
        //         // this.latitude  = position.coords.latitude;
        //         // this.longitude = position.coords.longitude;
        //         this.buttonAction = true

        //         const marker = {
        //             lat: this.center.lat,
        //             lng: this.center.lng
        //         };
        //         this.locationMarkers.push({ position: marker });
        //         this.locPlaces.push(this.existingPlace);
        //         this.center = marker;
        //         this.existingPlace = null;
        //     };

        //     const error = (err) => {
        //         console.log(error, err)
        //     };

        //     // This will open permission popup
        //     navigator.geolocation.getCurrentPosition(success, error);

        // },
        getLocation() {
            const success = (position) => {
                this.center.lat = position.coords.latitude
                this.center.lng = position.coords.longitude
                // this.latitude  = position.coords.latitude;
                // this.longitude = position.coords.longitude;
                this.buttonAction = true

                const marker = {
                    lat: this.center.lat,
                    lng: this.center.lng
                };
                this.locationMarkers.push({ position: marker });
                this.locPlaces.push(this.existingPlace);
                this.center = marker;
                this.existingPlace = null;
            };

            const error = (err) => {
                console.log(error, err)
                if (err.code === 1) {
                    this.showError = true
                }
            };

            // This will open permission popup
            navigator.geolocation.getCurrentPosition(success, error);

        },
        locateGeoLocation: function() {
            navigator.geolocation.getCurrentPosition(res => {
                this.center = {
                lat: res.coords.latitude,
                lng: res.coords.longitude
                };
            });
        },
        checkTime(i) {

            if (i < 10) {
                i = "0" + i;
            }
            return i;
        },

        startTime() {
            var today = new Date();
            var h = today.getHours();
            var m = today.getMinutes();
            // add a zero in front of numbers<10
            m = this.checkTime(m);
            this.time = `${h}:${m}`
        },
        imgUrlHandler() {
            if (!this.showImg) return null
            else return URL.createObjectURL(this.showImg)
        },
        toList(action) {
            this.$emit('register', action)
        },
        cancelNest() {
            setTimeout(() => {
                this.toList('list')
                }, 100)
            setTimeout(() => {
                this.sended = false
                }, 2500)
            
            
            
        },
        registerNest() {
            this.sended = true
            setTimeout(() => {
                this.toList('list')
                }, 2500)
            setTimeout(() => {
                this.sended = false
                }, 2500)
            
            
            
        },
    },

}
</script>

<style scoped>
.color-custom-default {
    color: #47BCC2
}
</style>
