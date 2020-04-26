<template>
    <div>
        <header class="header">
            <div class="container">
                <div class="flex-between">
                    <div>
                        <router-link to="/">Home</router-link>
                    </div>
                    <result-button v-on:getResult="getResult()" data-toggle="modal" data-target=".bd-example-modal-lg">
                        >
                    </result-button>
                </div>
            </div>
        </header>
        <div class="header-placeholder"></div>
        <CarTable />
        <div class="container">
            <div class="input-area">
                <h3 class="input-area__header">
                    Вагові коефіцієнти складових показника тактичної ефективності
                    перевезень
                </h3>
                <div class="input-area__section input-area__lambda flex-row">
                    <h4 class="title-value">λ11</h4>
                    <input
                            type="number"
                            class="input-area__input input-lambdaTac"
                            placeholder="λ11" v-model="tact_lambda[0]" @change="setLocal"/>
                    <h4 class="title-value">λ12</h4>
                    <input
                            type="number"
                            class="input-area__input input-lambdaTac"
                            placeholder="λ12" v-model="tact_lambda[1]" @change="setLocal"/>
                    <h4 class="title-value">λ13</h4>
                    <input
                            type="number"
                            class="input-area__input input-lambdaTac"
                            placeholder="λ13" v-model="tact_lambda[2]" @change="setLocal"/>
                    <h4 class="title-value">λ14</h4>
                    <input
                            type="number"
                            class="input-area__input input-lambdaTac"
                            placeholder="λ14" v-model="tact_lambda[3]" @change="setLocal"/>
                </div>
                <h3 class="input-area__header">Показники для тактичної ефективності</h3>
                <div class="input-area__section">
                    <h4 class="title-value">Доставлено чоловік a-дост</h4>
                    <input
                            type="number"
                            class="input-tact-ef"
                            title="достав. чол."
                            placeholder="достав. чол." v-model="tact_eff[0]" @change="setLocal"/>

                    <h4 class="title-value">Необхідно доставити чоловік a-вст</h4>
                    <input
                            type="number"
                            class="input-tact-ef"
                            title="Необхідно доставити чоловік"
                            placeholder="необ. достав. чол." v-model="tact_eff[1]" @change="setLocal"/>

                    <h4 class="title-value">Доставлено вантажу m-дост (ц)</h4>
                    <input
                            type="number"
                            class="input-tact-ef"
                            placeholder="достав. вантажу (ц)" v-model="tact_eff[2]" @change="setLocal"/>

                    <h4 class="title-value">
                        Маса вантажу, яку необхідно доставити m-вст (ц)
                    </h4>
                    <input
                            type="number"
                            class="input-tact-ef"
                            placeholder="необх. достав. вантаж (ц)" v-model="tact_eff[3]" @change="setLocal"/>

                    <h4 class="title-value">
                        Об'єм вантажу, який доставлено V-дост (м3)
                    </h4>
                    <input
                            type="number"
                            class="input-tact-ef"
                            title="достав. об'єм вантажу (м3)"
                            placeholder="достав. об'єм вантажу (м3)" v-model="tact_eff[4]" @change="setLocal"/>
                    <h4 class="title-value">
                        Об'єм вантажу, який необхідно доставити V-вст (м3)
                    </h4>
                    <input
                            type="number"
                            class="input-tact-ef"
                            title="достав. об'єм вантажу (м3)"
                            placeholder="достав. об'єм вантажу (м3)" v-model="tact_eff[5]" @change="setLocal"/>

                    <h4 class="title-value">Нормативно встановлений час t-вст (год)</h4>
                    <input
                            type="number"
                            class="input-tact-ef"
                            title="норм. встанов. час"
                            placeholder="норм. встанов. час" v-model="tact_eff[6]" @change="setLocal"/>
                    <h4 class="title-value">Фактичний час перевезення t-факт (год)</h4>
                    <input
                            type="number"
                            class="input-tact-ef"
                            title="фактичний час"
                            placeholder="фактичний час" v-model="tact_eff[7]" @change="setLocal"/>

                    <h4 class="title-value">Кількість техніки, яка прибула справною</h4>
                    <input
                            type="number"
                            class="input-tact-ef"
                            title="кількість техніки, яка прибула в справленому стані"
                            placeholder="кількість техніки" v-model="tact_eff[8]" @change="setLocal"/>
                </div>
                <h3 class="input-area__header">
                    Вагові коефіцієнти складових показника технічної ефективності
                    перевезень
                </h3>
                <div class="input-area__lambda flex-row">
                    <h4 class="title-value">λ21</h4>
                    <input
                            type="number"
                            class="input-area__input input-lambdaTechn"
                            placeholder="λ21" v-model="techn_lambda[0]" @change="setLocal"/>
                    <h4 class="title-value">λ22</h4>
                    <input
                            type="number"
                            class="input-area__input input-lambdaTechn"
                            placeholder="λ22" v-model="techn_lambda[1]" @change="setLocal"/>
                    <h4 class="title-value">λ23</h4>
                    <input
                            type="number"
                            class="input-area__input input-lambdaTechn"
                            placeholder="λ23" v-model="techn_lambda[2]" @change="setLocal"/>
                    <h4 class="title-value">λ24</h4>
                    <input
                            type="number"
                            class="input-area__input input-lambdaTechn"
                            placeholder="λ24" v-model="techn_lambda[3]" @change="setLocal"/>
                    <h4 class="title-value">λ25</h4>
                    <input
                            type="number"
                            class="input-area__input input-lambdaTechn"
                            placeholder="λ25" v-model="techn_lambda[4]" @change="setLocal"/>
                    <h4 class="title-value">λ26</h4>
                    <input
                            type="number"
                            class="input-area__input input-lambdaTechn"
                            placeholder="λ26" v-model="techn_lambda[5]" @change="setLocal"/>
                </div>
                <h3 class="input-area__header">Показники для технічної ефективності</h3>
                <h4 class="title-value">Планова відстань перевезень L-вст (км)</h4>
                <input
                        type="number"
                        class="input-techn-ef"
                        title="планова відстань перевезень"
                        placeholder="планова відстань перевезень" v-model="techn_eff[0]" @change="setLocal"/>
                <h4 class="title-value">Фактична відстань перевезень L-факт (км)</h4>
                <input
                        type="number"
                        class="input-techn-ef"
                        title="фактична відстань"
                        placeholder="фактична відстань" v-model="techn_eff[1]" @change="setLocal"/>
                <h3 class="input-area__header">Вагові показники для комплексної ефективності</h3>

                <div class="input-area__lambda flex-row">
                    <h4 class="title-value">λ1*</h4>
                    <input
                            type="number"
                            class="input-area__input input-lambdaComplex"
                            placeholder="λ1*" v-model="complex_lambda[0]" @change="setLocal"/>
                    <h4 class="title-value">λ2*</h4>
                    <input
                            type="number"
                            class="input-area__input input-lambdaComplex"
                            placeholder="λ2*" v-model="complex_lambda[1]" @change="setLocal"/>
                    <h4 class="title-value">λ3*</h4>
                    <input
                            type="number"
                            class="input-area__input input-lambdaComplex"
                            placeholder="λ3*" v-model="complex_lambda[2]" @change="setLocal"/>
                </div>
            </div>
            <div class="result-area">
                <result-button class="mt20" v-on:getResult="getResult()" data-toggle="modal"
                               data-target=".bd-example-modal-lg"></result-button>
                <div v-if="showResult" class="modal fade bd-example-modal-lg" tabindex="-1" role="dialog"
                     aria-labelledby="myLargeModalLabel" aria-hidden="true">
                    <div class="modal-dialog modal-lg">
                        <div class="modal-content">
                            <h3 class="input-area__header">Результат</h3>
                            <p class="result" v-html="resultObject">
                            </p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import CarTable from "./CarTable";
    import ResultButton from "./Result";

    export default {
        data() {
            return {
                showResult: false,
                resultObject: '',
                tact_eff: [3,3, 10,10, 20,20, 12,12, 3],
                tact_lambda: [0.65, 0.7, 0.8, 0.9],
                techn_lambda: [0.8,0.9,0.6,0.7,0.8,0.7],
                techn_eff: [1000,1200],
                complex_lambda: [0.7,0.6,0.8],
                L_vst: Number,
                L_fact: Number,
                fuel: {
                    0: {
                        type: "dp",
                        price: 28.7
                    },
                    1: {
                        type: "a95",
                        price: 29.7
                    },
                    2: {
                        type: "a92",
                        price: 28.7
                    }
                },
                M_vst: '', //вантажопід. машин
                V_vst: '', //обєм багажу машин
                A_vst: '', //пасажиромісткість машин
                X_vst: '', // к-сть техніки
                K_11: '', //коеф. еф. перевезень
                K_12: '', //коеф. дост вантажу
                K_13: '', //коеф. використання часу
                K_14: '', //коеф. тех готовності
                T_1: '', // тактична ефективність
                temp_array_tact: [],
                K_21: '', //коеф. готовн. техніки
                K_22: '', //коеф. запасу ходу
                K_23: '', //коеф. використання пробігу
                K_24: '', //коеф. використання пасажиромісткості
                K_25: '', //коев. вантажопідйомності
                K_26: '', //коеф. обємності
                T_2: '', // технічна ефективність
                temp_array_techn: [],
                C_31_f: '',// планова вартість пального
                C_32_f: '',//фактична вартість пального
                C_31_a: '',//планова армотизаційна вартість
                C_32_a: '',//фактична армотизаційна вартість
                complex_eff: 0, //комплескна ефективність
                T_3: '', // економiчна ефективність
                selected_cars: {
                    model: [],
                    speed: [],
                    lift: [],
                    passengers: [],
                    size_box: [],
                    spend_fuel: [],
                    type_fuel: [],
                    reserve_motor: [],
                    worked_time: [],
                    recovery_time: [],
                    coeff_ready: [],
                    fuel_price: [],
                    wear_factor_1000: [],
                    wear_factor_before: [],
                    wear_factor_after: [],
                    total_wear_factor_before: [],
                    total_wear_factor_after_plan: [],
                    total_wear_factor_after_fact: [],
                    term_service: [],
                    kilometrage: [],
                    car_cost: []
                }
            }
        },
        components: {
            CarTable,
            ResultButton
        },
        methods: {
            setLocal(){
                localStorage.setItem('tactEff', JSON.stringify(this.tact_eff));
                localStorage.setItem('tactLambda', JSON.stringify(this.tact_lambda));
                localStorage.setItem('techEff', JSON.stringify(this.techn_eff));
                localStorage.setItem('techLamba', JSON.stringify(this.techn_lambda));
                localStorage.setItem('complexLambda', JSON.stringify(this.complex_lambda));
            },
            outputResult() {
                this.K_11 = parseFloat(this.K_11).toFixed(3);
                this.K_12 = parseFloat(this.K_12).toFixed(3);
                this.K_13 = parseFloat(this.K_13).toFixed(3);
                this.K_14 = parseFloat(this.K_14).toFixed(3);
                this.K_21 = parseFloat(this.K_21).toFixed(3);
                this.K_22 = parseFloat(this.K_22).toFixed(3);
                this.K_23 = parseFloat(this.K_23).toFixed(3);
                this.K_24 = parseFloat(this.K_24).toFixed(3);
                this.K_25 = parseFloat(this.K_25).toFixed(3);
                this.K_26 = parseFloat(this.K_26).toFixed(3);
                this.T_1 = parseFloat(this.T_1).toFixed(3);
                this.T_2 = parseFloat(this.T_2).toFixed(3);
                this.C_31_a = parseFloat(this.C_31_a).toFixed(3);
                this.C_31_f = parseFloat(this.C_31_f).toFixed(3);
                this.C_32_a = parseFloat(this.C_32_a).toFixed(3);
                this.C_32_f = parseFloat(this.C_32_f).toFixed(3);
                this.T_3 = parseFloat(this.T_3).toFixed(3);
                this.complex_eff = parseFloat(this.complex_eff).toFixed(3);
                this.resultObject = "";

                this.resultObject += "Коеф. еф. перевезень особого складу     " + "<b>" + " K11=" + this.K_11 + "</b>" + '<br>';
                this.resultObject += "Коеф. еф. доставки вантажу              " + "<b>" + " K12=" + this.K_12 + "</b>" + '<br>';
                this.resultObject += "Коеф. часової еф. перевезень           " + "<b>" + "  K13=" + this.K_13 + "</b>" + '<br>';
                this.resultObject += "Коеф. тех. готовності технічних засобів " + "<b>" + " K14=" + this.K_14 + "</b>" + '<br> <br>';

                this.resultObject += "Тактична ефективність                   " + "<b>" + " T1=" + this.T_1 + "</b>" + '<br> <br>';

                this.resultObject += "Коеф. готовності техніки                " + "<b>" + " K21=" + this.K_21 + "</b>" + '<br>';
                this.resultObject += "Коеф. запасу ходу по моторесурсу        " + "<b>" + " K22=" + this.K_22 + "</b>" + '<br>';
                this.resultObject += "Коеф. використання пробігу              " + "<b>" + " K23=" + this.K_23 + "</b>" + '<br>';
                this.resultObject += "Коеф. використання пасажиромісткості    " + "<b>" + " K24=" + this.K_24 + "</b>" + '<br>';
                this.resultObject += "Коеф. використання вантажопідйомності   " + "<b>" + " K25=" + this.K_25 + "</b>" + '<br>';
                this.resultObject += "Коеф. використання об’ємності           " + "<b>" + " K26=" + this.K_26 + "</b>" + '<br> <br>';

                this.resultObject += "Технічна ефективність                   " + "<b>" + " T2=" + this.T_2 + "</b>" + '<br> <br>';

                this.resultObject += "Планова вартість пального               " + "<b>" + " C*31=" + this.C_31_f + "</b>" + '<br>';
                this.resultObject += "Планова вартість амортизаційного зносу  " + "<b>" + " C*32=" + this.C_31_a + "</b>" + '<br>';
                this.resultObject += "Фактична вартість пального              " + "<b>" + " C31=" + this.C_32_f + "</b>" + '<br>';
                this.resultObject += "Фактична вартість амортизаційного зносу " + "<b>" + " C32=" + this.C_32_a + "</b>" + '<br> <br>';

                this.resultObject += "Економічна ефективність                 " + "<b>" + " T3=" + this.T_3 + "</b>" + '<br> <br>';

                this.resultObject += "Комплексна ефективність                 " + "<b>" + " Е=" + this.complex_eff + "</b>" + '<br> <br>';

            },
            getValueFromInputs() {

                this.L_vst = this.techn_eff[0];
                this.L_fact = this.techn_eff[1];


            },
            getSelectedCars() {
                let row_car_area = document.getElementsByClassName("row-car");
                let table_speed = document.getElementsByClassName("table__speed");
                let table_model = document.getElementsByClassName("table__model");
                let table_lift = document.getElementsByClassName("table__lift");
                let table_passengers = document.getElementsByClassName("table__passengers");
                let table_size_box = document.getElementsByClassName("table__size_box");
                let table_spend_fuel = document.getElementsByClassName("table__spend_fuel");
                let table_type_fuel = document.getElementsByClassName("table__type_fuel");
                let table_reserve_motor = document.getElementsByClassName("table__reserve_motor");
                let table_worked_time = document.getElementsByClassName("table__worked_time");
                let table_recovery_time = document.getElementsByClassName("table__recovery_time");
                let table_wear_factor_1000 = document.getElementsByClassName("table__wear_factor_1000");
                let table_wear_factor_before = document.getElementsByClassName("table__wear_factor_before");
                let table_wear_factor_after = document.getElementsByClassName("table__wear_factor_after");
                let table_term_service = document.getElementsByClassName("table__term_service");
                let table_kilometrage = document.getElementsByClassName("table__kilometrage");
                let table_car_cost = document.getElementsByClassName("table__car_cost");
                Object.keys(this.selected_cars).forEach(element => {
                    this.selected_cars[element] = [];
                });
                for (let index = 0; index < row_car_area.length; index++) {
                    let chek_area = row_car_area[index].querySelector('.check-car');
                    if (chek_area.checked) {
                        this.selected_cars.model.push(table_model[index].value);
                        this.selected_cars.speed.push(parseFloat(table_speed[index].value));
                        this.selected_cars.lift.push(parseFloat(table_lift[index].value));
                        this.selected_cars.passengers.push(parseFloat(table_passengers[index].value));
                        this.selected_cars.size_box.push(parseFloat(table_size_box[index].value));
                        this.selected_cars.spend_fuel.push(parseFloat(table_spend_fuel[index].value));
                        this.selected_cars.type_fuel.push(table_type_fuel[index].value);
                        this.selected_cars.worked_time.push(parseFloat(table_worked_time[index].value));
                        this.selected_cars.reserve_motor.push(parseFloat(table_reserve_motor[index].value));
                        this.selected_cars.recovery_time.push(parseFloat(table_recovery_time[index].value));
                        this.selected_cars.wear_factor_1000.push(parseFloat(table_wear_factor_1000[index].value));
                        this.selected_cars.wear_factor_after.push(parseFloat(table_wear_factor_after[index].value));
                        this.selected_cars.wear_factor_before.push(parseFloat(table_wear_factor_before[index].value));
                        this.selected_cars.term_service.push(parseFloat(table_term_service[index].value));
                        this.selected_cars.kilometrage.push(parseFloat(table_kilometrage[index].value));
                        this.selected_cars.car_cost.push(parseFloat(table_car_cost[index].value));
                    }
                }
                //computed this.selected_cars.fuel_price
                for (let index = 0; index < this.selected_cars.model.length; index++) {
                    for (let index_fuel = 0; index_fuel < Object.keys(this.fuel).length; index_fuel++) {
                        if (this.selected_cars.type_fuel[index] === this.fuel[index_fuel].type) {
                            this.selected_cars.fuel_price[index] = this.fuel[index_fuel].price;
                        }
                    }
                    //computed this.selected_cars.coeff_ready
                    this.selected_cars.coeff_ready[index] = this.selected_cars.worked_time[index] / (this.selected_cars.worked_time[index] + this.selected_cars.recovery_time[index]);


                    //computed this.selected_cars wear factory
                    this.selected_cars.total_wear_factor_before[index] = 1 - (((this.selected_cars.wear_factor_1000[index] * this.selected_cars.kilometrage[index]) + (this.selected_cars.wear_factor_before[index] * this.selected_cars.term_service[index])) / 100);
                    this.selected_cars.total_wear_factor_after_plan[index] = 1 - (((this.selected_cars.wear_factor_1000[index] * (this.selected_cars.kilometrage[index] + (this.L_vst / 1000))) + (this.selected_cars.wear_factor_after[index] * this.selected_cars.term_service[index])) / 100);

                    this.selected_cars.total_wear_factor_after_fact[index] = 1 - (((this.selected_cars.wear_factor_1000[index] * (this.selected_cars.kilometrage[index] + (this.L_fact / 1000))) + (this.selected_cars.wear_factor_after[index] * this.selected_cars.term_service[index])) / 100);
                }
            },
            getValueTact() {
                this.M_vst = 0;
                this.V_vst = 0;
                this.A_vst = 0;
                this.X_vst = 0;
                this.K_11 = 0;
                this.K_12 = 0;
                this.K_13 = 0;
                this.K_14 = 0;
                this.T_1 = 0;
                this.temp_array_tact = [];
                for (let index = 0; index < this.selected_cars.model.length; index++) {
                    this.X_vst += 1;
                }
                this.A_vst = this.tact_eff[1];
                this.M_vst = this.tact_eff[3];
                this.V_vst = this.tact_eff[5];

                this.K_11 = this.tact_eff[0] / this.A_vst;
                this.K_12 = (this.tact_eff[2] * this.tact_eff[4]) / (this.M_vst * this.V_vst);
                this.K_13 = this.tact_eff[6] / this.tact_eff[7];
                this.K_14 = this.tact_eff[8] / this.X_vst;

                this.temp_array_tact.push(this.K_11, this.K_12, this.K_13, this.K_14);

                for (let index = 0; index < this.tact_lambda.length; index++) {
                    this.T_1 += this.tact_lambda[index] * this.temp_array_tact[index];
                }
            },
            getValueTechn() {
                this.K_21 = 0;
                this.K_22 = 0;
                this.K_23 = 0;
                this.K_24 = 0;
                this.K_25 = 0;
                this.K_26 = 0;
                this.T_2 = 0;
                let temp_reserve_motor_fact = 0;
                let temp_reserve_motor = 0;
                let koef_ready_total = 0;
                let temp_M_vst = 0;
                let temp_V_vst = 0;
                let temp_A_vst = 0;

                this.temp_array_techn = [];

                for (let index = 0; index < this.selected_cars.model.length; index++) {
                    temp_reserve_motor_fact += this.selected_cars.reserve_motor[index] - this.L_fact;
                    temp_reserve_motor += this.selected_cars.reserve_motor[index];
                    koef_ready_total += this.selected_cars.coeff_ready[index];
                    temp_M_vst += this.selected_cars.lift[index];
                    temp_V_vst += this.selected_cars.size_box[index];
                    temp_A_vst += this.selected_cars.passengers[index];

                }
                this.K_21 = koef_ready_total / this.X_vst;
                this.K_22 = temp_reserve_motor_fact / temp_reserve_motor;
                this.K_23 = this.L_fact / this.L_vst;
                if (temp_A_vst === 0) {
                    this.K_24 = 1
                } else {
                    this.K_24 = this.tact_eff[0] / temp_A_vst;
                }
                if (temp_M_vst === 0) {
                    this.K_25 = 1
                } else {
                    this.K_25 = this.tact_eff[0] / temp_A_vst;
                }
                if (temp_V_vst === 0) {
                    this.K_26 = 1
                } else {
                    this.K_26 = this.tact_eff[0] / temp_A_vst;
                }
                this.temp_array_techn.push(this.K_21, this.K_22, this.K_23, this.K_24, this.K_25, this.K_26);

                for (let index = 0; index < this.techn_lambda.length; index++) {
                    this.T_2 += this.techn_lambda[index] * this.temp_array_techn[index];
                }
            },
            getValueEconomy() {
                this.C_31_f = 0;
                this.C_31_a = 0;
                this.C_32_f = 0;
                this.C_32_a = 0;
                this.T_3 = 0;
                for (let index = 0; index < this.selected_cars.model.length; index++) {
                    this.C_31_f += this.L_vst * this.selected_cars.spend_fuel[index] * this.selected_cars.fuel_price[index];
                    this.C_32_f += this.L_fact * this.selected_cars.spend_fuel[index] * this.selected_cars.fuel_price[index];
                    this.C_31_a += this.selected_cars.car_cost[index] * (this.selected_cars.total_wear_factor_before[index] - this.selected_cars.total_wear_factor_after_plan[index]);
                    this.C_32_a += this.selected_cars.car_cost[index] * (this.selected_cars.total_wear_factor_before[index] - this.selected_cars.total_wear_factor_after_fact[index]);
                }
                this.C_31_f /= 100;
                this.C_32_f /= 100;
                this.T_3 = (this.C_31_f + this.C_31_a) / (this.C_32_f + this.C_32_a);
            },
            getComplexEff() {
                this.complex_eff = this.T_1 * this.complex_lambda[0] + this.T_2 * this.complex_lambda[1] + this.T_3 * this.complex_lambda[2];
            },
            getResult() {
                this.getSelectedCars();
                if (this.selected_cars.model.length < 1) {
                    alert("Виберіть техніку")
                } else {
                    this.showResult = true;
                    this.getValueFromInputs();
                    this.getValueTact();
                    this.getValueTechn();
                    this.getValueEconomy();
                    this.getComplexEff();
                    this.outputResult();
                }
            }
        },
        created() {
            let localTact = localStorage.getItem('tactEff');
            let localTactLambda = localStorage.getItem('tactLambda');
            let localTechn = localStorage.getItem('techEff');
            let localTechnLambda = localStorage.getItem('techLamba');
            let localComplexLambda = localStorage.getItem('complexLambda');

            if (localTact !== null){
                this.tact_eff = JSON.parse(localTact)
            }
            if (localTactLambda !== null){
                this.tact_lambda = JSON.parse(localTactLambda)
            }
            if (localTechn !== null){
                this.techn_eff = JSON.parse(localTechn)
            }
            if (localTechnLambda !== null){
                this.techn_lambda = JSON.parse(localTechnLambda)
            }
            if (localComplexLambda !== null){
                this.complex_lambda = JSON.parse(localComplexLambda)
            }
        }

    }
</script>

<style scoped lang="scss">
    .header {
        height: 100px;
        background: #fff;
        border-bottom: 1px solid #ddadff;
        position: sticky;
        top: 0;

        .container {
            height: 100%;
        }

    }

    .flex-between {
        display: flex;
        justify-content: space-between;
        align-items: center;
        height: 100%;
    }

    .title-value {
        font-size: 18px;
    }

    .input-area {
        input {
            width: 150px;
        }

        &__header {
            margin-top: 20px;
            margin-bottom: 20px;
            font-size: 24px;
        }

        &__lambda input {
            margin-right: 5px;
            margin-left: 5px;
            max-width: 70px;
        }
    }

    .flex-row {
        display: flex;
        flex-wrap: wrap;
    }

    .modal-content {
        padding: 20px;
    }

    .mt20 {
        margin-top: 20px;
    }
</style>