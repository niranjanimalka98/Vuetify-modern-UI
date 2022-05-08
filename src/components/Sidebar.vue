
<template>
    
    <nav>
        <v-app-bar color="#23262D" dark app class ="line" >

            <h2>Point Of Sale System</h2>
            <div>
                <VueClock/>
            </div>
            
            
            <!--<v-chip class="ma-2" color="grey darken-1" pill>Dashboard
                <v-icon right small color="cyan">fas fa-chevron-circle-down</v-icon>
            </v-chip>
            <v-chip class="ma-2" color="grey darken-1" pill>Reports
               <v-icon right small color="cyan">fas fa-chevron-circle-down</v-icon> 
            </v-chip>
            <v-chip class="ma-2" color="grey darken-1" pill>Orders
               <v-icon right small color="cyan">fas fa-chevron-circle-down</v-icon> 
            </v-chip>-->
            <v-spacer></v-spacer>
            <v-text-field filled dense rounded label="Search" prepend-inner-icon="fas fa-search" 
            class="mt-6 mr-2" sm="2"></v-text-field>
            <v-btn fab color="cyan" elevation="0" class="mr-2" small>
                <v-icon color="white">far fa-question-circle</v-icon>
            </v-btn>
            <v-btn fab color="orange" elevation="0" small>
                <v-icon color="white">far fa-user-circle</v-icon>
            </v-btn>
        </v-app-bar>
        <v-navigation-drawer v-model="drawer" dark app mini-variant mini-variant-width="150" color="#23262D">
            <v-list>
                <v-list-item-group color="cyan">
                    <v-list-item class="mb-4">
                        <v-list-item-content align="center">
                            <v-icon color="#4169E1" align="center" x-large>fas fa-laptop-code</v-icon>
                            
                            <v-list-item-subtitle align="center" class="caption" style="margin-top: 20px; color: #4169E1;"><strong>NJN SOFT Solution</strong></v-list-item-subtitle>
                        </v-list-item-content>
                    </v-list-item>
                </v-list-item-group>
                <v-list-item-group v-model="selectedItem" color="#C0C0C0">
                   <v-list-item v-for="(item, i) in items" :key="i">
                        <v-list-item-content align="center">
                           <v-icon v-text="item.icon" class="mb-3" align="center" ></v-icon>
                           <v-list-item-subtitle v-text="item.text" align="center" class="caption"></v-list-item-subtitle>
                        </v-list-item-content>
                    </v-list-item> 
                </v-list-item-group>

            </v-list>
        </v-navigation-drawer>
    </nav>
</template>

<script>
import VueClock from '../components/Clock.vue';
export default{
    
    

    data: () => ({
        drawer: null,
        selectedItem: 0,
        items: [
            {text: 'Dashboard', icon: 'fas fa-tachometer-alt'},
            {text: 'Reports', icon: 'fas fa-file-alt'},
            {text: 'Stock', icon: 'fas fa-store'},
            {text: 'Sales', icon: 'fas fa-shopping-bag'},
            {text: 'User Reports', icon: 'fas fa-user-tag'},
            {text: 'Settings', icon: 'fas fa-cogs'},
            
        
        ]
        
    }),
    components:{VueClock},
};

    
</script>
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Kumbh+Sans&display=swap');
h2{
    font-family: 'Kumbh Sans', sans-serif;
    
    
}
</style>
