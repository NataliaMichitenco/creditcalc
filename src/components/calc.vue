<template>
    <div class="banner center">
        <h1 class="banner__h1">Кредитный калькулятор</h1>
        <p class="banner__text">Позволяет легко и быстро рассчитать график платежей по интересующему вас кредиту, оценить свои возможности погасить долг без просрочек. Введите несколько параметров кредита, подберите удобные для вас условия и сравните их с предложениями разных банков.</p>
        <div class="banner__calc">
            <input class="banner__calc_input" type="number" v-model="credit" placeholder="Сумма кредита"> <br>
            <input class="banner__calc_input" type="number" v-model="period" placeholder="Срок кредита"> <br>
            <input class="banner__calc_input" type="number" v-model="percent" placeholder="Процентная ставка"> <br>
            <p class="banner__calc_result">Ежемесячный плотеж: {{ result.payByMonth !== 'NaN' ? result.payByMonth : 0 }}</p>
            <p class="banner__calc_total">Общая сумма выплаты по кредиту: {{ result.total !== 'NaN' ? result.total : 0 }}</p>
        </div>
        <div class="banner__img">
            <img class="" src="../assets/img/shubham-dhage-nG1LnDkt3HA-unsplash 1.jpg" alt="img">
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                credit: null,
                percent: null,
                period: null,
            }
        },
        computed: {
            result() {
                const principal = parseFloat(this.credit);
                const interestRate = parseFloat(this.percent) / 100 / 12;
                const loanTermMonths = parseFloat(this.period);

                const numerator = principal * interestRate * Math.pow(1 +interestRate, loanTermMonths);
                const denominator = Math.pow(1 + interestRate, loanTermMonths) - 1;
                const payByMonth = (numerator / denominator).toFixed(2);
                const total = (payByMonth * loanTermMonths).toFixed(2);
                return { payByMonth, total };

            }
        }
    }
</script>

<style lang="scss" scoped>
input[type=number]::-webkit-inner-spin-button,
input[type=number]::-webkit-outer-spin-button {
    -webkit-appearance: none;
    margin: 0;
}
.banner {
display: flex;
justify-content: center;
align-content: center;
flex-wrap: wrap;
align-items: center;
gap: 40px;

    &__h1 {
        color: rgba(236, 82, 11, 0.804);
    }
    &__text{
        color: rgb(170, 72, 19);
        font-size: 26px;
        text-align: center;
    }
    &__calc {
        &_result {
            color: rgb(170, 72, 19);
            font-size: 20px;
        }
        &_total {
            color:rgb(170, 72, 19);
            font-size: 20px;
        }
        &_input {
            border: 1px solid rgb(170, 72, 19);
            border-radius: 10px;
            background: rgb(170, 72, 19);
            color: black;
            font-weight: 600;
            font-size: 20px;
            width: 230px;
            height: 40px;
            margin-bottom: 15px;
            padding-left: 30px;
        }
        &_input::placeholder {
            color: rgb(45, 43, 43);
        }
    }

}

</style>