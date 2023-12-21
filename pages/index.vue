<template>
    <div>
        <h1>タスク一覧テスト2
        </h1>
        <hr>
        <NuxtLink to="/other"></NuxtLink>
    </div>
    <v-container class="fill-height">
        <v-data-table
            v-model:items-per-page="itemsPerPage"
            :headers="headers"
            :items="tasks"
            item-value="id"
            class="elevation-1"
        >
        <template v-slot:item.actions="{ item }">
            <v-icon
                size="small"
                @click="deleteItem(item.id)"
                >
                mdi-delete
            </v-icon>
        </template>
        </v-data-table>
    </v-container>
    
    <v-row class="justify-end">
        <v-dialog v-model="dialog" persistent width="1024">
            <template v-slot:activator="{ props }">
                <v-btn color="blue-darken-4" v-bind="props">タスクを追加する</v-btn>
            </template>
            <v-card>
                <v-card-title>
                <span class="text-h5">タスク入力</span>
                </v-card-title>
                <v-card-text>
                <v-container>
                    <v-row>
                        <v-col cols="12">
                            <v-select
                            :items="['AAA', 'BBB', 'CCC', 'DDD']"
                            label="プロジェクト名*"
                            required
                            ></v-select>
                        </v-col>
                        <v-col cols="12">
                            <v-text-field
                            label="タスク内容*"
                            required
                            ></v-text-field>
                        </v-col>
                        <v-col cols="12" sm="6">
                            <v-select
                            :items="['0-17', '18-29', '30-54', '54+']"
                            label="期日*"
                            required
                            ></v-select>
                        </v-col>
                        <v-col cols="12" sm="6">
                            <v-autocomplete
                            :items="['未着手', '進行中', '完了']"
                            label="状態"
                            ></v-autocomplete>
                        </v-col>
                    </v-row>
                </v-container>
                <small>*indicates required field</small>
                </v-card-text>
                <v-card-actions>
                <v-spacer></v-spacer>
                <v-btn color="blue-grey-darken-4" variant="text" @click="dialog = false">
                    閉じる
                </v-btn>
                <v-btn color="blue-darken-1" variant="text" @click="">
                    登録する
                </v-btn>
                </v-card-actions>
            </v-card>
        </v-dialog>
    </v-row>
</template>

<script>
  export default {
    methods: {
        deleteItem(item){
        alert( item.id + "番のデータを削除します");
        }
    },
    data() {
      return {
        dialog: false,
        itemsPerPage: 5,
        headers: [
            {
                title: 'ID',
                align: 'start',
                key: 'id',
                width: 1,
            },
            {title: 'プロジェクト名',align: 'start',sortable: false, key: 'name',width: 200,},
            { title: 'タスク内容', align: 'start',sortable: false, key: 'task' },
            { title: '期日', align: 'end', key: 'duedate' },
            { title: '状態', align: 'end',sortable: false, key: 'status' },
            { title: '操作', align: 'end',sortable: false, key: 'actions' },
        ],
        tasks: [
          {
            id: '1',
            name: 'AAA',
            task: 'フレームワーク作成',
            duedate: '2024/01/01',
            status: '未着手',
            confirm: ''
          },
          {
            id: '2',
            name: 'BBB',
            task: 'フレームワーク作成',
            duedate: '2024/01/01',
            status: '未着手',
            confirm: ''
          },
          {
            id: '3',
            name: 'CCC',
            task: 'フレームワーク作成',
            duedate: '2024/01/01',
            status: '未着手',
            confirm: ''
          },
          {
            id: '4',
            name: 'DDD',
            task: 'フレームワーク作成',
            duedate: '2024/01/01',
            status: '未着手',
            confirm: ''
          },
          {
            id: '5',
            name: 'EEE',
            task: 'フレームワーク作成',
            duedate: '2024/01/01',
            status: '未着手',
            confirm: ''
          },
          {
            id: '6',
            name: 'FFF',
            task: 'フレームワーク作成',
            duedate: '2024/01/01',
            status: '未着手',
            confirm: ''
          },
        ],
      }
    },
  }
</script>