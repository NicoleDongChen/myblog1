<template>
    <div>
        <div id="container" v-comment:id="ArticlesId"></div>
    </div>
</template>

<script>
import Gitment from '../assets/gitment/gitment.js'
import '../assets/gitment/default.css'
export default {
    props: ['ArticlesId'],
    data () {
        return {
            
        }
    },
    mounted () {
        
    },
    directives: {
        comment: {
            bind: function(el, binding){
                const myTheme = {
                    render(state, instance) {
                        const container = document.createElement('div')
                        container.lang = "en-US"
                        container.className = 'gitment-container gitment-root-container'
                        // container.appendChild(instance.renderHeader(state, instance))
                        container.appendChild(instance.renderEditor(state, instance))
                        container.appendChild(instance.renderComments(state, instance))
                        // container.appendChild(instance.renderFooter(state, instance))
                        return container
                    },
                }
                var gitment = new Gitment({
                    id:location.href ,
                    owner: 'NicoleDongChen',
                    repo: 'myapp',
                    oauth: {
                        client_id: '43b6c1343b22afefd77b',
                        client_secret: '2bf1b500855ee26daaec386973f7c13ebb03ee4f',
                    },
                    theme: myTheme
                })
                gitment.render(el)

            }
        }
    }
}
</script>

<style scoped>
</style>