<template>
  <div>
    <div class="defcon-container">
      <h1 class="title is-1">DEFCON</h1>
      <div class="columns">
        <div class="column is-narrow">
          <div v-for="def in defcons" v-bind:key="def.name" v-bind:style="[def.baseStyles, def.isActive ? def.overridedStyles: '']" v-bind:id="def.name" class="defcon" v-on:click="setActive(def.name)">
            {{ def.title }}
          </div>
        </div>
        <div class="column is-narrow">
          <div v-for="def in defcons" v-bind:key="def.name" v-if="def.isActive" class="descr">
            <div class="card">
              <header class="card-header">
                <p class="card-header-title">
                  {{def.description.title}}
                </p>
              </header>
              <div class="card-content">
                <div class="content">
                  <ul>
                    <li v-for="item in def.description.list" :key="item" class="line">{{item}}</li>
                  </ul>
                  <table class="table is-bordered is-fullwidth">
                    <tr>
                      <td>
                        <ul>
                          <li v-for="item in def.description.table.col1" :key="item">{{item}}</li>
                        </ul>
                      </td>
                      <td>
                        <ul>
                          <li v-for="item in def.description.table.col2" :key="item">{{item}}</li>
                        </ul>
                      </td>
                    </tr>
                  </table>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Defcon',
  methods: {
    setActive (selectDef) {
      let id = selectDef.substr(selectDef.length - 1, 1) - 1
      let previousDef = this.defcons[this.previousDefId]
      if (previousDef) {
        previousDef.isActive = false
      }
      let def = this.defcons[id]
      if (!def.isActive) {
        def.isActive = true
        this.previousDefId = id
      }
    }
  },
  data () {
    return {
      previousDefId: 4,
      defcons: [
        {
          name: 'defcon1',
          title: '1',
          baseStyles: {
            backgroundColor: '#e36d6d',
            color: 'darkslategrey',
            opacity: 0.5
          },
          overridedStyles: {
            backgroundColor: 'red',
            color: 'black',
            opacity: 1,
            fontWeight: 'bold',
            boxShadow: '0px 0px 20px black'
          },
          description: {
            title: 'War',
            list: ['Current iteration is stopped.', 'Meetings during the day to identity issues and have a visibility on progress.', 'PO and SM can interrupt anyone if necessary.', 'Review and put into production process have to be followed carefully.'],
            table: {
              col1: ['Majors fixes but urgent to do in production with impacts outside of the team.', 'Need to follow work in progress with many teams.'],
              col2: ['Full Kanban']
            }
          },
          isActive: false
        },
        {
          name: 'defcon2',
          title: '2',
          baseStyles: {
            backgroundColor: '#fee2aa',
            color: 'darkslategrey',
            opacity: 0.5
          },
          overridedStyles: {
            backgroundColor: 'orangered',
            color: 'black',
            opacity: 1,
            fontWeight: 'bold',
            boxShadow: '0px 0px 20px black'
          },
          description: {
            title: 'General rallying',
            list: ['Current iteration is stopped.', 'Meetings during the day to identity issues and have a visibility on progress.', 'PO and SM can interrupt anyone if necessary.', 'Review and put into production process have to be followed carefully.'],
            table: {
              col1: ['Majors fixes but urgent to do in production.', 'Need more than 2 persons to deal with hotfixes flow.'],
              col2: ['Full Kanban']
            }
          },
          isActive: false
        },
        {
          name: 'defcon3',
          title: '3',
          baseStyles: {
            backgroundColor: '#f3f88d',
            color: 'darkslategrey',
            opacity: 0.5
          },
          overridedStyles: {
            backgroundColor: 'yellow',
            color: 'black',
            opacity: 1,
            fontWeight: 'bold',
            boxShadow: '0px 0px 20px black'
          },
          description: {
            title: 'Instant response',
            list: ['All exterior demands are managed by PO and SM only.', 'PM and SM interrupt developers that matches with functional scope needed.', 'Only Hotfixes are taken into account. The demand is critical and need to be managed immediately. Investigation allow to determine risk level and severity.'],
            table: {
              col1: ['Minors fixes but urgent to do in production', 'Need more than one person to deal with hotfixes flow'],
              col2: ['Scrum for the team', 'Kanban for interruptible developers']
            }
          },
          isActive: false
        },
        {
          name: 'defcon4',
          title: '4',
          baseStyles: {
            backgroundColor: '#b9fcac',
            color: 'darkslategrey',
            opacity: 0.5
          },
          overridedStyles: {
            backgroundColor: 'green',
            color: 'black',
            opacity: 1,
            fontWeight: 'bold',
            boxShadow: '0px 0px 20px black'
          },
          description: {
            title: 'Increased attention',
            list: ['All exterior demands are managed by PO and SM only.', 'A developer is named as interruptible for investigation and Hofixes. Only this developers can be disturb by PO or SM.', 'Only Hotfixes are taken into account.', 'The demand is critical and need to be managed immediately.', 'Prior investigation allow to determine risk and severity level.'],
            table: {
              col1: ['Highlights outside the team', 'Some HotFixes fixable by only one person'],
              col2: ['Scrum for the team', 'Kanban for interruptible developers']
            }
          },
          isActive: false
        },
        {
          name: 'defcon5',
          title: '5',
          baseStyles: {
            backgroundColor: '#b2b7fe',
            color: 'darkslategrey',
            opacity: 0.5
          },
          overridedStyles: {
            backgroundColor: 'blue',
            color: 'black',
            opacity: 1,
            fontWeight: 'bold',
            boxShadow: '0px 0px 20px black'
          },
          description: {
            title: 'Peace',
            list: ['All exterior demands are managed by PO and SM only.', 'PO and SM don\'t interrupt developers. They use the stand up meeting to exchange.', '1 hour max investigation could be done, but no unexpected development.'],
            table: {
              col1: ['Default level', 'No HotFix'],
              col2: ['Full SCRUM']
            }
          },
          isActive: true
        }
      ]
    }
  }
}
</script>

<style scoped>
.title {
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  font-size: 30px;
}

.defcon {
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 30px;
  width: 100px;
}

.defcon-container{
  margin: 20px;
  display: grid;
  grid-column-gap: 10px;
  grid-row-gap: 2px;
  float: left;
}

.descr {
  display: flow;
  width: 500px;
}

.line {
  text-align: justify;
}
</style>
