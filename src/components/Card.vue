<template>
    <div class="col-card col-11 col-sm-8 col-md-6 col-lg-4 col-xl-3 mb-4">
        <div class="row">
            <div class="col-12">
                <div v-bind:id="'carousel-' + index" class="carousel slide" data-ride="carousel">
                    <ol class="carousel-indicators">
                        <li :data-target="'#carousel-' + index" :data-slide-to="indexImagem" v-bind:class="{ active: indexImagem==0 }" v-for="(photos, indexImagem) of produto.photos " :key="indexImagem"></li>
                    </ol>
                    <div class="carousel-inner">
                        <div class="carousel-item " v-bind:class="{ active: indexImagem==0 }" v-for="(photos, indexImagem) of produto.photos " :key="indexImagem">
                            <img :src="(photos)" class="d-block w-100" alt="...">
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div class="row">
            <div class="col-12">
                <div class="card-product d-flex flex-column">            
                    <div class="row">
                        <div class="col-12">
                            <h1 class="name mb-2">{{ produto.name }}</h1>    
                        </div>                                
                    </div>
                    <div class="row">
                        <div class="col-12">  
                            <h5 class="distrito mb-1">{{ produto.address.district }}</h5> 
                        </div>
                    </div>                            
                    <div class="row"> 
                        <div class="col-12">  
                            <h5 class="cidade mb-3">{{ produto.address.city }}</h5>
                        </div>
                    </div> 
                    <div class="row"> 
                        <div class="col-12 detalhes">
                            <p>
                                <i class="fas fa-key"></i>
                                Apartamentos de {{ printArray(produto.units.usable_areas) }} m²
                            </p>
                        </div>
                        <div class="col-12 detalhes" v-if="(Array.isArray(produto.units.en_suites) && produto.units.en_suites.length > 0 && !verificaAreaZero(produto.units.en_suites)) || (!Array.isArray(produto.units.en_suites) && produto.units.en_suites != null && produto.units.en_suites > 0)">                              
                            <p>
                                <i class="fas fa-bed"></i>
                                {{ printArray(produto.units.en_suites) }} suítes
                            </p>
                        </div>                        
                        <div class="col-12 detalhes" v-if="produto.address.geo_location.latitude <= -21.211 && produto.address.geo_location.latitude >= -21.269 && produto.address.geo_location.longitude <= -47.780 && produto.address.geo_location.longitude >= -47.857">  
                            <p>
                                <i class="fas fa-map-marker-alt"></i>
                                 Localização privilegiada
                            </p>
                        </div>
                    </div> 
                    <div class="row mt-auto">                 
                        <div class="col-12">  
                            <a class="btn button-cta w-100">Ver mais</a>
                        </div>
                    </div> 
                </div>
            </div>
        </div>
    </div>
</template>

<script>


export default {
    props: {
        produto: Object,
        index: Number
    },
    methods: {
        verificaAreaZero(u){
            u.forEach(element => {
                if(element < 1 ){
                    return true
                }
            })
        },

        printArray(u){
            var txtSuites = " ";

            if (Array.isArray(u)){                
                if (u.length <= 2) {
                    u.forEach((element, chave) => {
                        if((u.length-1) == chave && element > 0){                
                            txtSuites = (txtSuites + element + " ")
                        } else if(element > 0){
                            txtSuites = (txtSuites + element + " e ")
                        }                    
                    });  
                } else {
                    u.forEach((element, chave) => {
                        if((u.length-1) == chave && element > 0){                
                            txtSuites = (txtSuites + element + " ")
                        } else if(element > 0){
                            txtSuites = (txtSuites + element + ", ")
                        }                    
                    });   
                }                             
            } else {
                txtSuites = (u);
            }
            
            return txtSuites;
        }
    },
    computed: {
        
    }
};
</script>

<style scoped>
.card-product {
    background-color: white;
    border-radius: 15px;
    box-shadow: 1px 1px 5px 2px rgb(0 0 0 / 30%);
    min-height: 100%;
    padding: 30px 30px;
    position: relative;
    min-height: 320px;
    margin-top: -15px;
}

.card-product .name {
    font-weight: 700;
    font-size: 1.8rem;
    line-height: 0.9em;
    color: black;
}

.card-product .distrito, .cidade {
    font-weight: 500;
    font-size: 0.9rem;
    color: #727272;
}

.card-product .distrito {
    font-size: 1.05rem;
}

.card-product .detalhes>p {
    font-size: 0.9rem;
    font-weight: 500;
    color: black;
    margin-bottom: 0.5rem;
}

.card-product .detalhes>p>i {
    color: #ed7203;
    margin-right: 3px;
}

.card-product .button-cta {
    background-color: #ed7203;
    border-radius: 12px;
    font-size: 0.72rem;
    color: white;
    font-weight: 600;   
}

.carousel-inner {
    border-radius: 15px 15px 0px 0px;
}

.carousel-indicators {
    justify-content: flex-end;
}

.carousel-indicators li {
    border-radius: 50%;
    width: 8px;
    height: 8px;
}

.carousel-item img{
    height: 143px;
    width: 100%;
}

@media (max-width: 1199px){
    .carousel-item img{
        height: 160px;
    }
}

</style>