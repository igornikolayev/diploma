<template>
    <div class="container-fluid">
        <div class="table">
            <table class="table table-bordered table-hover car-table">
                <caption>
                    Список техніки
                </caption>
                <thead>
                <tr class="">
                    <th class="table__header">Вибрати</th>
                    <th class="table__header">Марка техніки</th>
                    <th class="table__header">Середня швидкість руху км/год</th>
                    <th class="table__header">Вантажо- підйомн. (ц)</th>
                    <th class="table__header">Пасажиро- місткість, чол</th>
                    <th class="table__header">Об'єм кузова, м3</th>
                    <th class="table__header">Середня витрата пального, л/100км</th>
                    <th class="table__header">Тип пального (a95, a92, dp)</th>
                    <th class="table__header">Запас ходу по моторе- сурсу, км</th>
                    <th class="table__header">Час в працезд. стані, доба</th>
                    <th class="table__header">Час відновл., доба</th>
                    <th class="table__header">Плановий показник зносу на 1000км</th>
                    <th class="table__header">
                        Плановий показник зносу перед вибуттям
                    </th>
                    <th class="table__header">
                        Плановий показник зносу після прибуття
                    </th>
                    <th class="table__header">Строк експлуа- тації, рік</th>
                    <th class="table__header">Пробіг тис. км.</th>
                    <th class="table__header">Первісна вартість, тис. грн.</th>
                </tr>
                </thead>

                <tbody class="table__content">
                <tr v-for="(car, id) in cars" :key="id" class=" row-car ">
                    <td><input type="checkbox" class="check-car"/></td>
                    <td>
                        <input class="table__model" type="text" v-model="car.model" @blur="setLocal" />
                    </td>
                    <td>
                        <input class="table__speed" type="number" v-model="car.speed" @change="setLocal"/>
                    </td>
                    <td>
                        <input class="table__lift" type="number" v-model="car.lift" @change="setLocal"/>
                    </td>
                    <td>
                        <input
                                class="table__passengers"
                                type="number"
                                v-model="car.passengers"
                                @change="setLocal"
                        />
                    </td>
                    <td>
                        <input
                                class="table__size_box"
                                type="number"
                                v-model="car.size_box"
                                @change="setLocal"
                        />
                    </td>
                    <td>
                        <input
                                class="table__spend_fuel"
                                type="number"
                                v-model="car.spend_fuel"
                                @change="setLocal"
                        />
                    </td>
                    <td>
                        <input
                                class="table__type_fuel"
                                type="text"
                                v-model="car.type_fuel"
                                @change="setLocal"
                        />
                    </td>
                    <td>
                        <input
                                class="table__reserve_motor"
                                type="number"
                                v-model="car.reserve_motor"
                                @change="setLocal"
                        />
                    </td>
                    <td>
                        <input
                                class="table__worked_time"
                                type="number"
                                v-model="car.worked_time"
                                @change="setLocal"
                        />
                    </td>
                    <td>
                        <input
                                class="table__recovery_time"
                                type="number"
                                v-model="car.recovery_time"
                                @change="setLocal"
                        />
                    </td>
                    <td>
                        <input
                                class="table__wear_factor_1000"
                                type="number"
                                v-model="car.wear_factor_1000"
                                @change="setLocal"
                        />
                    </td>
                    <td>
                        <input
                                class="table__wear_factor_before"
                                type="number"
                                v-model="car.wear_factor_before"
                                @change="setLocal"
                        />
                    </td>
                    <td>
                        <input
                                class="table__wear_factor_after"
                                type="number"
                                v-model="car.wear_factor_after"
                                @change="setLocal"
                        />
                    </td>
                    <td>
                        <input
                                class="table__term_service"
                                type="number"
                                v-model="car.term_service"
                                @change="setLocal"
                        />
                    </td>
                    <td>
                        <input
                                class="table__kilometrage"
                                type="number"
                                v-model="car.kilometrage"
                                @change="setLocal"
                        />
                    </td>
                    <td>
                        <input
                                class="table__car_cost"
                                type="number"
                                v-model="car.car_cost"
                                @change="setLocal"
                        />
                    </td>
                </tr>
                </tbody>
            </table>
            <add-car v-on:add-car="addCar()"/>
        </div>
    </div>
</template>

<script>
    import AddCar from "./AddCar";

    export default {
        data() {
            return {
                cars: [],
                model: [
                    "УАЗ-315195",
                    "УАЗ-315195",
                    "УАЗ-315195",
                    "УАЗ-315195",
                    "Volk. Amarok",
                    "Volk. Amarok",
                    "ВАЗ-21230",
                    "ВАЗ-21230",
                    "Land Rover",
                    "Land Rover",
                    "ГАЗ-32213",
                    "ГАЗ-32213",
                    "Volkswagen Т5",
                    "Volkswagen Т5",
                    "КРАЗ-6322",
                    "КРАЗ-6322",
                    "КРАЗ-6322",
                    "КРАЗ-6322",
                    "КРАЗ-6322",
                    "КРАЗ-6322",
                    "КРАЗ-6322",
                    "КРАЗ-6322",
                    "КРАЗ-6322",
                    "КРАЗ-6322",
                    "КРАЗ-6322",
                    "КРАЗ-6322"
                ],
                speed: [
                    60,
                    60,
                    60,
                    60,
                    70,
                    70,
                    70,
                    70,
                    60,
                    60,
                    80,
                    80,
                    90,
                    90,
                    50,
                    50,
                    50,
                    50,
                    50,
                    50,
                    50,
                    50,
                    50,
                    50,
                    50,
                    50
                ],
                lift: [
                    0,
                    0,
                    0,
                    0,
                    12,
                    12,
                    0,
                    0,
                    5,
                    5,
                    0,
                    0,
                    0,
                    0,
                    100,
                    100,
                    100,
                    100,
                    100,
                    100,
                    100,
                    0,
                    0,
                    0,
                    0,
                    0
                ],
                passengers: [
                    7,
                    7,
                    7,
                    7,
                    5,
                    5,
                    5,
                    5,
                    5,
                    5,
                    13,
                    13,
                    9,
                    9,
                    3,
                    3,
                    3,
                    3,
                    3,
                    3,
                    3,
                    25,
                    25,
                    25,
                    25,
                    25
                ],
                size_box: [
                    0,
                    0,
                    0,
                    0,
                    3,
                    3,
                    0,
                    0,
                    1,
                    1,
                    0,
                    0,
                    0,
                    0,
                    25,
                    25,
                    25,
                    25,
                    25,
                    25,
                    25,
                    25,
                    25,
                    25,
                    25,
                    25
                ],
                spend_fuel: [
                    14,
                    14,
                    14,
                    14,
                    10,
                    10,
                    11,
                    11,
                    12,
                    12,
                    11,
                    11,
                    8,
                    8,
                    40,
                    40,
                    40,
                    40,
                    40,
                    40,
                    40,
                    40,
                    40,
                    40,
                    40,
                    40
                ],
                type_fuel: [
                    "a92",
                    "a92",
                    "a92",
                    "a92",
                    "a95",
                    "a95",
                    "a95",
                    "a95",
                    "dp",
                    "dp",
                    "a95",
                    "a95",
                    "dp",
                    "dp",
                    "dp",
                    "dp",
                    "dp",
                    "dp",
                    "dp",
                    "dp",
                    "dp",
                    "dp",
                    "dp",
                    "dp",
                    "dp",
                    "dp"
                ],
                reserve_motor: [
                    3200,
                    3600,
                    4900,
                    6200,
                    6500,
                    4200,
                    3800,
                    3100,
                    5400,
                    3500,
                    4600,
                    5600,
                    3800,
                    4200,
                    4200,
                    3700,
                    3300,
                    3800,
                    3600,
                    3700,
                    5100,
                    6600,
                    4800,
                    5000,
                    4200,
                    3700
                ],
                worked_time: [
                    235,
                    289,
                    295,
                    292,
                    278,
                    290,
                    292,
                    251,
                    293,
                    270,
                    295,
                    298,
                    210,
                    280,
                    293,
                    270,
                    225,
                    290,
                    278,
                    288,
                    268,
                    298,
                    285,
                    300,
                    320,
                    270
                ],
                recovery_time: [
                    65,
                    11,
                    5,
                    8,
                    22,
                    10,
                    8,
                    49,
                    7,
                    30,
                    2,
                    30,
                    5,
                    2,
                    90,
                    20,
                    7,
                    30,
                    75,
                    10,
                    22,
                    12,
                    32,
                    2,
                    15,
                    0
                ],
                coeff_ready: [
                    0.78,
                    0.96,
                    0.98,
                    0.97,
                    0.93,
                    0.97,
                    0.97,
                    0.84,
                    0.98,
                    0.9,
                    0.99,
                    0.9,
                    0,
                    98,
                    0.99,
                    0.7,
                    0.93,
                    0.98,
                    0.9,
                    0.75,
                    0.97,
                    0.93,
                    0.96,
                    0.89,
                    0.99,
                    0.95,
                    1
                ],
                fuel_price: [],
                wear_factor_1000: [
                    0.25,
                    0.25,
                    0.25,
                    0.25,
                    0.25,
                    0.25,
                    0.25,
                    0.25,
                    0.25,
                    0.25,
                    0.25,
                    0.25,
                    0.25,
                    0.25,
                    0.25,
                    0.25,
                    0.25,
                    0.25,
                    0.25,
                    0.25,
                    0.25,
                    0.25,
                    0.25,
                    0.25,
                    0.25,
                    0.25
                ],
                wear_factor_before: [
                    1.244,
                    1.244,
                    1.244,
                    1.244,
                    1.244,
                    1.244,
                    1.244,
                    1.244,
                    1.244,
                    1.244,
                    1.244,
                    1.244,
                    1.244,
                    1.244,
                    1.244,
                    1.244,
                    1.244,
                    1.244,
                    1.244,
                    1.244,
                    1.244,
                    1.244,
                    1.244,
                    1.244,
                    1.244,
                    1.244
                ],
                wear_factor_after: [
                    1.239,
                    1.239,
                    1.239,
                    1.239,
                    1.239,
                    1.239,
                    1.239,
                    1.239,
                    1.239,
                    1.239,
                    1.239,
                    1.239,
                    1.239,
                    1.239,
                    1.239,
                    1.239,
                    1.239,
                    1.239,
                    1.239,
                    1.239,
                    1.239,
                    1.239,
                    1.239,
                    1.239,
                    1.239,
                    1.239
                ],
                total_wear_factor_before: [],
                total_wear_factor_after_plan: [],
                total_wear_factor_after_fact: [],
                term_service: [
                    9,
                    6,
                    7,
                    8,
                    4,
                    4,
                    7,
                    7,
                    7,
                    6,
                    14,
                    19,
                    4,
                    4,
                    4,
                    4,
                    4,
                    3,
                    3,
                    3,
                    4,
                    4,
                    4,
                    5,
                    5,
                    5
                ],
                kilometrage: [
                    105.15,
                    28.9,
                    75.715,
                    68.074,
                    14.014,
                    17.12,
                    198.2,
                    245.83,
                    53.021,
                    42.876,
                    119.66,
                    327.8,
                    88.415,
                    75.939,
                    33.812,
                    14.234,
                    12.877,
                    29.564,
                    4.124,
                    17.158,
                    17.567,
                    15.432,
                    13.824,
                    28.152,
                    19.003,
                    24.986
                ],
                car_cost: [
                    62.129,
                    75.7,
                    72.32,
                    72.32,
                    624.823,
                    624.823,
                    159.925,
                    157.802,
                    356.075,
                    343.845,
                    59.824,
                    50.694,
                    728.84,
                    766.919,
                    929.166,
                    929.166,
                    929.166,
                    879.236,
                    879.236,
                    879.236,
                    921.567,
                    921.567,
                    921.567,
                    877.913,
                    877.913,
                    877.913
                ]

            }
        },
        components: {
            AddCar
        },
        methods: {
            addCar() {
                this.cars.push({
                    model : '',
                    speed : '',
                    lift : '',
                    passengers: '',
                    size_box : '',
                    spend_fuel : '',
                    type_fuel : '',
                    reserve_motor : '',
                    worked_time : '',
                    recovery_time : '',
                    coeff_ready : '',
                    fuel_price : '',
                    wear_factor_1000 : '',
                    wear_factor_before : '',
                    wear_factor_after : '',
                    total_wear_factor_before : '',
                    total_wear_factor_after_plan : '',
                    total_wear_factor_after_fact : '',
                    term_service : '',
                    kilometrage : '',
                    car_cost : ''
                })
            },
            setLocal () {
                localStorage.setItem('cars', JSON.stringify(this.cars));
            }
        },
        created() {
            let localCars = localStorage.getItem('cars')
            if (localCars !== null){
                this.cars = JSON.parse(localCars)
            } else {
                for (let index = 0; index< this.model.length; index++) {
                    let tempObj = {
                        model: this.model[index],
                        speed: this.speed[index],
                        lift: this.lift[index],
                        passengers: this.passengers[index],
                        size_box: this.size_box[index],
                        spend_fuel: this.spend_fuel[index],
                        type_fuel: this.type_fuel[index],
                        reserve_motor: this.reserve_motor[index],
                        worked_time: this.worked_time[index],
                        recovery_time: this.recovery_time[index],
                        coeff_ready: this.coeff_ready[index],
                        fuel_price: this.fuel_price[index],
                        wear_factor_1000: this.wear_factor_1000[index],
                        wear_factor_before: this.wear_factor_before[index],
                        wear_factor_after: this.wear_factor_after[index],
                        total_wear_factor_before: this.total_wear_factor_before[index],
                        total_wear_factor_after_plan: this.total_wear_factor_after_plan[index],
                        total_wear_factor_after_fact: this.total_wear_factor_after_fact[index],
                        term_service: this.term_service[index],
                        kilometrage: this.kilometrage[index],
                        car_cost: this.car_cost[index]
                    }
                    this.cars.push(tempObj)
                }
            }
        }
    }
</script>

<style lang="scss">
    .table {
        max-width: 100vw;
        overflow-x: scroll;

        &__header {
            width: 150px !important;
        }
    }

    .row input {
        box-sizing: border-box;
        width: 50px;
    }

    .car-table {
        text-align: center;
    }

    .car-table input {
        width: 100%;
    }

</style>