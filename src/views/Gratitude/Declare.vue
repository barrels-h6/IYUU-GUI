<template>
    <div>
        <el-card class="main-card">
            <div slot="header" class="clearfix">
                <b>问题反馈</b>
                <el-link class="extra_link" @click="shellOpen(issue)">
                    查看所有反馈者 <i class="el-icon-link" />
                </el-link>
            </div>
            <div>
                受限于开发者个人水平，在实际开发过程中可能存在各种问题未被发现。<br>
                如果你在使用过程发现问题，请考虑通过以下途径进行反馈。
                <el-divider />
                <ul>
                    <li class="report_way">
                        IYUU-GUI 官方仓库（含源码、Issue、Wiki）：
                        <el-link type="primary" @click="shellOpen('https://github.com/Rhilip/IYUU-GUI')">
                            https://github.com/Rhilip/IYUU-GUI
                        </el-link>
                    </li>
                    <li class="report_way">
                        IYUUAutoReseed 源码仓库：
                        <el-link type="primary" @click="shellOpen('https://gitee.com/ledc/IYUUAutoReseed')">
                            gitee源码仓库
                        </el-link>
                        <el-divider direction="vertical" />
                        <el-link type="primary" @click="shellOpen('https://github.com/ledccn/IYUUAutoReseed')">
                            GitHub源码仓库
                        </el-link>
                    </li>
                    <li class="report_way">
                        IYUUAutoReseed 官方教程：
                        <el-link type="primary" @click="shellOpen('https://gitee.com/ledc/IYUUAutoReseed/tree/master/wiki')">
                            https://gitee.com/ledc/IYUUAutoReseed/tree/master/wiki
                        </el-link>
                    </li>
                    <li class="report_way">
                        IYUUAutoReseed 官方问答社区：
                        <el-link type="primary" @click="shellOpen('http://wenda.iyuu.cn')">
                            http://wenda.iyuu.cn
                        </el-link>
                    </li>
                    <li class="report_way">
                        【IYUU自动辅种交流】QQ群：
                        859882209 （一群，已满）
                        <el-divider direction="vertical" />
                        931954050 （二群）
                    </li>
                </ul>
            </div>
        </el-card>
        <el-card class="main-card">
            <div slot="header" class="clearfix">
                <b>特别鸣谢</b>
                <el-link class="extra_link" @click="shellOpen(contributors)">
                    查看所有协作者 <i class="el-icon-link" />
                </el-link>
            </div>
            <div>
                <span id="thanks_note">
                    在项目的开发和测试中，他们给予了很多帮助和支持，在此表示感谢。<br>
                    列表中未能一一列出所有给予帮助的同学，也对他们表示感谢，如有遗漏敬请谅解。<br>
                </span>
                <el-divider />
                <ShowPersons :persons="thanksData.developers"
                             person-type-note="原型开发"
                             tag-type="warning"
                             icon-class="el-icon-magic-stick" />
                <ShowPersons :persons="thanksData.testers"
                             person-type-note="内测成员"
                             tag-type="info"
                             icon-class="el-icon-mouse" />
                <ShowPersons :persons="thanksData.operators"
                             person-type-note="后期维护"
                             tag-type=""
                             icon-class="el-icon-brush" />
            </div>
        </el-card>
        <el-card class="main-card">
            <div slot="header" class="clearfix">
                <b>项目参考和引用</b>
                <el-link class="extra_link" @click="shellOpen(dependencies)">
                    查看所有构建依赖 <i class="el-icon-link" />
                </el-link>
            </div>
            <div>
                <span id="refs_note">
                    首先感谢 @ledccn 开发的辅种软件 IYUUAutoReseed ，并提供相应 API 使得二次开发更为方便。 <br>
                    在可视化开发过程中， @ledccn 也给予本人（@Rhilip）很多帮助。
                    <el-divider />
                    此外，IYUU GUI 的诞生也是建立在这些项目基础之上，在此一并感谢所有项目的参与人员，感谢他们的付出！
                </span>
                <div id="refs_table" style="margin-top: 10px">
                    <el-table :data="refsData" stripe>
                        <el-table-column
                                label="项目名"
                                width="240">
                            <template slot-scope="scope">
                                <el-tooltip class="item" effect="dark" :content="scope.row.note" placement="right">
                                    <span style="margin-left: 10px">{{ scope.row.name }}</span>
                                </el-tooltip>
                            </template>
                        </el-table-column>
                        <el-table-column
                                prop="version"
                                label="版本" width="80" />
                        <el-table-column
                                label="链接">
                            <template slot-scope="scope">
                                <el-link type="primary" @click="shellOpen(scope.row.link)">
                                    {{ scope.row.link }}
                                </el-link>
                            </template>
                        </el-table-column>
                    </el-table>
                </div>
            </div>
        </el-card>
    </div>
</template>

<script>
    import {shellOpen} from '../../plugins/common'
import ShowPersons from "../../components/Gratitude/ShowPersons";
export default {
  name: 'Declare',
  components: {ShowPersons},
  data () {
    return {
      shellOpen: shellOpen,
      dependencies: 'https://github.com/Rhilip/IYUU-GUI/network/dependencies',
      issue: 'https://github.com/Rhilip/IYUU-GUI/issues',
      contributors: 'https://github.com/Rhilip/IYUU-GUI/graphs/contributors',

      // 用户鸣谢
      thanksData: {
        // 原始贡献者
        developers: [
          'ledccn', 'Rhilip',
        ],

        // 后续参与维护
        operators: [
        ],

        // 测试阶段成员
        testers: [
          'Throne', '路在脚下', '樊夫', 'ice羽毛', '再见', 'al6', 'delete', '诗书琴画',
          '承世', '甘蔗地里犯了错', 'oO子非鱼oO', '浣熊'
        ]
      },

      // 项目引用
      refsData: [
        {
          name: 'IYUUAutoReseed',
          version: '1.8.6',
          note: 'IYUUAutoReseed 官方项目（基于PHP）',
          link: 'https://github.com/ledccn/IYUUAutoReseed/'
        },
        {
          name: 'Electron',
          version: '8.4.0',
          note: '使用 JavaScript，HTML 和 CSS 构建跨平台的桌面应用程序。',
          link: 'https://www.electronjs.org/'
        },
        {
          name: 'Vue CLI Plugin Electron Builder',
          version: '2.0.0',
          note: 'Easily Build Your Vue.js App For Desktop With Electron',
          link: 'https://nklayman.github.io/vue-cli-plugin-electron-builder/'
        },
        {
          name: 'Vue.js',
          version: '2.5.16',
          note: '渐进式JavaScript 框架',
          link: 'https://cn.vuejs.org/index.html'
        },
        {
          name: 'Vuex',
          version: '3.0.1',
          note: '专为 Vue.js 应用程序开发的状态管理模式',
          link: 'https://vuex.vuejs.org/zh/'
        },
        {
          name: 'Vue Router',
          version: '3.0.1',
          note: 'Vue.js 官方的路由管理器',
          link: 'https://router.vuejs.org/zh/'
        },
        {
          name: 'Element',
          version: '2.13.2',
          note: '一套为开发者、设计师和产品经理准备的基于 Vue 2.0 的桌面端组件库',
          link: 'https://element.eleme.cn/#/zh-CN'
        },
        {
          name: 'axios',
          version: '0.18.0',
          note: 'Promise based HTTP client for the browser and node.js',
          link: 'https://github.com/axios/axios'
        },
        {
          name: 'Lodash',
          version: '4.17.19',
          note: 'A modern JavaScript utility library delivering modularity, performance & extras.',
          link: 'https://lodash.com/'
        },
        {
          name: 'Day.js',
          version: '1.8.29',
          note: 'Fast 2kB alternative to Moment.js with the same modern API',
          link: 'https://dayjs.gitee.io/zh-CN/'
        },
        {
          name: 'jsonar',
          version: '1.8.0',
          note: 'Convert JSON to PHP native Array.',
          link: 'https://github.com/oknoorap/jsonar'
        },
        {
          name: 'FileSaver.js',
          version: '2.0.2',
          note: 'An HTML5 saveAs() FileSaver implementation',
          link: 'https://github.com/eligrey/FileSaver.js'
        },

        // ▲▲▲▲其他项目（直接相关的）请添加到此处以上▲▲▲▲
        {
          name: '....',
          version: '....',
          note: '其他底层项目'
          // link: '....'
        }
      ]
    }
  }
}
</script>

<style scoped>
    .extra_link {
        float: right;
        padding: 3px 0
    }

    .report_way {
        margin: 5px 0;
    }
</style>
