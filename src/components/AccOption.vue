<script setup>

import { computed } from 'vue'
import { useStore } from 'vuex'
import Toggle from '@vueform/toggle'

const store = useStore()
const user = computed(() => store.state.user.user)
</script>
    <template>
    <form class="px-5">
        <div class="my-2">
            <strong>Добавлять задачи в начало списка</strong>
            <div class="flex mt-2">
                <Toggle
                v-model="user.add_task_to_begin"
                  @change="hasChanged = true"
                  class="outline-none ring-0"
                  :classes="{ toggleOn: 'bg-blue-400 border-blue-400 justify-start text-white', container: 'focus:ring-0' }"
                />
                <a class="ml-2" v-if="user.add_task_to_begin === true">Вкл.</a>
                <a class="ml-2" v-if="user.add_task_to_begin === false">Выкл.</a>
            </div>
        </div>
        <div class="my-2">
            <strong>Первая неделя с 1 января</strong>
            <div class="flex mt-2">
                <Toggle
                v-model="user.cal_number_of_first_week"
                  @change="hasChanged = true"
                  class="outline-none ring-0"
                  :classes="{ toggleOn: 'bg-blue-400 border-blue-400 justify-start text-white', container: 'focus:ring-0' }"
                />
                <a class="ml-2" v-if="user.cal_number_of_first_week === true">Вкл.</a>
                <a class="ml-2" v-if="user.cal_number_of_first_week === false">Выкл.</a>
            </div>
        </div>
        <div class="my-2">
            <strong>Показывать номера недель в календаре</strong>
            <div class="flex mt-2">
                <Toggle
                v-model="user.cal_show_week_number"
                  @change="hasChanged = true"
                  class="outline-none ring-0"
                  :classes="{ toggleOn: 'bg-blue-400 border-blue-400 justify-start text-white', container: 'focus:ring-0' }"
                />
                <a class="ml-2" v-if="user.cal_show_week_number === true">Вкл.</a>
                <a class="ml-2" v-if="user.cal_show_week_number === false">Выкл.</a>
            </div>
        </div>
        <div class="my-2">
            <strong>Показываать раздел Просрочено</strong>
            <div class="flex mt-2">
                <Toggle
                  @change="hasChanged = true"
                  class="outline-none ring-0"
                  :classes="{ toggleOn: 'bg-blue-400 border-blue-400 justify-start text-white', container: 'focus:ring-0' }"
                />
                <a class="ml-2" v-if="user.nav_show_overdue === true">Вкл.</a>
                <a class="ml-2">Выкл.</a>
            </div>
        </div>
        <div class="my-2">
            <strong>Показывать количество задач</strong>
            <div class="flex mt-2">
                <Toggle
                  @change="hasChanged = true"
                  class="outline-none ring-0"
                  :classes="{ toggleOn: 'bg-blue-400 border-blue-400 justify-start text-white', container: 'focus:ring-0' }"
                />
                <a class="ml-2" v-if="user.nav_show_summary === true">Вкл.</a>
                <a class="ml-2">Выкл.</a>
            </div>
        </div>
        <div class="my-2">
            <strong>Язык</strong>
            <div class="flex mt-2">
                <select v-model="user.language">
                    <option value="russian">Русский</option>
                    <option>Английский</option>
                </select>
            </div>
        </div>
        <div class="my-2">
            <strong>Напиоминание о задаче за </strong>
            <div class="flex mt-2">
                <select>
                    <option value="0">0 мин</option>
                    <option value="10">10 мин</option>
                    <option value="15">15 мин</option>
                    <option value="30">30 мин</option>
                    <option value="60">60 мин</option>
                </select>
            </div>
        </div>
    </form>
    </template>
