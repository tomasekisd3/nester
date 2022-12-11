<template>
  <div>
    <v-card class="pa-10 mt-6 mx-2">
        <v-row>
            <v-col cols="12" class="d-flex justify-space-between">
                <div class="text-h4">Lista de nidos</div>
                <div><v-btn dark color="#47BCC2" @click="register()">registrar nido</v-btn></div>
            </v-col>
            <v-col cols="12">
                <v-data-table
                    :headers="headers"
                    :items="nests"
                    class="elevation-1"
                    item-key="id"
                >
                   <template v-slot:[`item.actions`]>
                    <div>
                         <v-icon>mdi-dots-vertical</v-icon>
                    </div>
                   </template> 
                   <template v-slot:[`item.image`]="{ item }">
                    <div>
                        <v-btn icon>
                            <v-icon color="#47BCC2" @click="showImg(item.image)">
                                mdi-eye
                            </v-icon>
                        </v-btn>
                    </div>
                   </template> 
                </v-data-table>
            </v-col>
        </v-row>
        
    </v-card>
    <v-dialog v-model="showImgDialog" persistent max-width="500">
        <v-card>
            <v-card-title class="headline">Imagen</v-card-title>
            <v-card-text>
                <v-col cols="12">Esta foto fue subida el día del registro</v-col>
                <v-col cols="12">
                    <div style="border: 2px solid #47BCC2">
                        <v-img min-width="300" min-height="300" :src="imgAux" />
                    </div>
                </v-col>
            </v-card-text>
            <v-card-actions>
                <v-col cols="12" class="d-flex justify-center">
                    <v-btn dark color="secondary" @click="closeImg()">Cerrar</v-btn>
                </v-col>
            </v-card-actions>
        </v-card>
    </v-dialog>
  </div>
</template>

<script>
export default {
    name: 'NestsList',
    data() {
        return {
            showImgDialog: false,
            imgAux: '',
            headers: [
                { text: 'Fecha registro', value: 'fechaCreacion' },
                { text: 'Hora registro', value: 'tiempoCreacion' },
                { text: 'Dirección', value: 'direccion' },
                { text: 'Comuna', value: 'comuna' },
                { text: 'Región', value: 'region' },
                { text: 'País', value: 'pais' },
                { text: 'Foto', value: 'image', sortable: false },
                { text: 'Acciones', value: 'actions', sortable: false, align: 'center' },
            ],
            nests: [
                {
                    id: '1',
                    fechaCreacion: '2022-08-12',
                    tiempoCreacion: '23:40',
                    direccion: 'Av Independencia 400',
                    comuna: 'Recoleta',
                    region: 'RM',
                    pais: 'Chile',
                    image: 'https://previews.123rf.com/images/fotogenix/fotogenix1603/fotogenix160300165/56324316-la-cotorra-myiopsitta-monachus-tambi%C3%A9n-conocido-como-el-loro-quaker-visto-fuera-de-su-nido-.jpg'

                },
                {
                    id: '2',
                    fechaCreacion: '2022-01-10',
                    tiempoCreacion: '23:40',
                    direccion: 'Av Manquehue 222',
                    comuna: 'Las Condes',
                    region: 'RM',
                    pais: 'Chile',
                    image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ8nK647-oXQnmQJrkALB8mI7FCzJktl3x4Mw&usqp=CAU'

                },
                {
                    id: '3',
                    fechaCreacion: '2022-03-13',
                    tiempoCreacion: '23:40',
                    direccion: 'Av Siempre Viva 742',
                    comuna: 'Santiago',
                    region: 'RM',
                    pais: 'Chile',
                    image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSNZ6YyoiSymUjqx928iU-kJlS6ZnH_y6buYWT33ZlPoaWj4KIxFv-VbUl2bJTr97hKkrE&usqp=CAU'

                },
                {
                    id: '4',
                    fechaCreacion: '2022-09-22',
                    tiempoCreacion: '23:40',
                    direccion: 'Psje Cerro Blanco 453',
                    comuna: 'Cerro Blanco',
                    region: 'RM',
                    pais: 'Chile',
                    image: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ9GKZpnMeB0OeemRn-HyzTFN3KncSk-3tuvLgffLMyMYIcVaK_FvOvDUEyzBbTe22Y1uY&usqp=CAU'

                },
                {
                    id: '5',
                    fechaCreacion: '2022-04-15',
                    tiempoCreacion: '23:40',
                    direccion: 'Av Manuel Antonio Matta 467',
                    comuna: 'Quilicura',
                    region: 'RM',
                    pais: 'Chile',
                    image: 'https://s1.eestatic.com/2019/10/07/actualidad/actualidad_434966785_134635814_1706x960.jpg'

                },
            ],
        }
    },
    methods: {
        showImg(image) {
            this.imgAux = image
            this.showImgDialog = true
        },
        closeImg() {
            this.imgAux = ''
            this.showImgDialog = false
        },
        register() {
            this.$emit('register', 'register')
        },
    },

}
</script>
