<template>
    <div class="col-card col-11 col-sm-8 col-md-6 col-lg-4 col-xl-3 mb-4">
        <div class="card-product d-flex flex-column">
            <div class="row card-slide">
                <div id="carouselExampleIndicators" class="carousel slide" data-ride="carousel">
                    <ol class="carousel-indicators">
                        <li data-target="#carouselExampleIndicators" data-slide-to="0" class="active"></li>
                        <li data-target="#carouselExampleIndicators" data-slide-to="1"></li>
                    </ol>
                    <div class="carousel-inner">
                        <div class="carousel-item active">
                            <img :src="require('../assets/teste/a.jpg')" class="d-block w-100" alt="...">
                        </div>
                        <div class="carousel-item">
                            <img :src="require('../assets/teste/b.jpg')" class="d-block w-100" alt="...">
                        </div>
                    </div>
                </div>
            </div>
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
                    
                </div>
                <div class="col-12 detalhes" v-if="produto.units.en_suites!=null">  
                    <p>
                        <i class="fas fa-bed"></i>
                        <!-- {{ printSuites(produto.units.en_suites) }} suítes -->
                        {{ produto.units.en_suites }} suítes
                    </p>
                </div>
                <div class="col-12 detalhes">  
                    
                </div>
            </div> 
            <div class="row mt-auto">                 
                <div class="col-12">  
                    <a class="btn button-cta w-100">Ver mais</a>
                </div>
            </div> 
        </div>
    </div>
</template>

<script>


export default {
    props: {
        produto: Object
    },
    computed: {
        // printSuites: function(u){
        //     var txtSuites;

        //     array.forEach(element => {
        //         console.log(element)
        //         element = (txtSuites + element + ", ")
        //     });

        //     return txtSuites;
        // }
    }
};

// function printSuites(u){
//     var txtSuites;

//     array.forEach(element => {
//         element = (txtSuites + element + ", ")
//     });

//     return txtSuites;
// }
</script>

<style scoped>
.card-product {
    background-color: white;
    border-radius: 15px;
    box-shadow: 1px 1px 5px 2px rgb(0 0 0 / 30%);
    min-height: 100%;
    padding: 30px 30px;
    /* margin-top: 150px; */
    position: relative;
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

.card-product .detalhes>p>i {
    color: #ed7203;
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
    box-shadow: 1px 1px 5px 2px rgb(0 0 0 / 30%);
}

.card-slide {
    position: absolute;
    top: -150px;
    left: 15px;
    width: 100%;
    z-index: -10;    
}

.col-card {
    margin-top: 150px;
}
</style>