<template>
  <div
    class="h-screen w-screen bg-gradient-to-r from-blue-500 to-gray-200 p-20"
  >
    <div class="grid grid-cols-12 gap-20 h-full">
      <div class="col-span-12 lg:col-span-4 h-full">
        <div class="bg-white bg-opacity-30 w-full h-full rounded-xl p-8">
          <div class="flex flex-col space-y-5">
            <img
              class="w-full h-32"
              src="https://kiloex.io/static/svg/bbe1ac23.svg"
              alt="logo"
            />
            <input
              v-model="tradingPoints"
              class="w-full rounded shadow-md px-4 py-2 focus:outline-none"
              placeholder="Trading Points"
              type="number"
            />
            <div class="flex flex-col space-y-3">
              <h2 class="text-3xl font-semibold">Result:</h2>
              <hr />
              <p class="font-semibold">
                Volume:
                {{ Math.round((tradingPoints / 24.5) * 1000).toLocaleString() }}
                $
              </p>
              <p class="font-semibold">
                Fee Spent:
                {{
                  Math.round(
                    (Math.round((tradingPoints / 24.5) * 1000) * 0.1) / 100
                  ).toLocaleString()
                }}
                $
              </p>
              <p class="font-semibold">
                Estimate Tokens:
                {{
                  Math.round(
                    (tradingPoints / 603000000) * 40000000
                  ).toLocaleString()
                }}
                $KILOEX
              </p>
            </div>
          </div>
        </div>
      </div>
      <div class="col-span-12 lg:col-span-8 h-full">
        <div class="bg-white bg-opacity-30 w-full h-full rounded-xl p-8">
          <div class="flex flex-col space-y-10">
            <h1 class="text-5xl font-bold">Formula:</h1>
            <hr class="my-10" />
            <div>
              <p>Volume = ( Trading Points ÷ 24.5 ) x 1,000</p>
              <p>
                Fee Spent = (( Trading Points ÷ 24.5 ) x 1,000) x ( 0.1 ÷ 100 )
              </p>
              <p>
                Estimate KILOEX (Genesis Season) = ( Trading Points /
                603,000,000 ) x 40,000,000
              </p>
            </div>
          </div>
          <div class="flex flex-col space-y-10 mt-20">
            <h1 class="text-5xl font-bold">Note:</h1>
            <hr class="my-10" />
            <div>
              <p>
                1. This is just an estimate that doesn't include the VIP fee
                discount.
              </p>
              <p>
                2. Estimate KILOEX Token is based on a linear formula with
                calculated from one of the Discord admins mentioned for total
                points (603m).
              </p>
              <p>
                3. Estimate Token subject to change due to Discord admin
                mentioned that each type of point will have a different value.
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const tradingPoints = ref(null);
</script>
