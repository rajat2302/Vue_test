<template>
    <v-app id="sandbox">
        <v-navigation-drawer
            :clipped="primaryDrawer.clipped"
            :floating="primaryDrawer.floating"
            :mini-variant="primaryDrawer.mini"
            :permanent="primaryDrawer.type === 'permanent'"
            :temporary="primaryDrawer.type === 'temporary'"
            app
            overflow
            v-model="primaryDrawer.model"
        ></v-navigation-drawer>

        <v-app-bar :clipped-left="primaryDrawer.clipped" app>
            <v-app-bar-nav-icon
                @click.stop="primaryDrawer.model = !primaryDrawer.model"
                v-if="primaryDrawer.type !== 'permanent'"
            ></v-app-bar-nav-icon>
            <v-toolbar-title>Vuetify</v-toolbar-title>
        </v-app-bar>

        <v-main>
            <v-container fluid>
                <v-row align="center" justify="center">
                    <v-col cols="10">
                        <v-card>
                            <v-card-text>
                                <v-row>
                                    <v-col cols="12" md="6">
                                        <span>Scheme</span>
                                        <v-switch
                                            label="Dark"
                                            primary
                                            v-model="$vuetify.theme.dark"
                                        ></v-switch>
                                    </v-col>
                                    <v-col cols="12" md="6">
                                        <span>Drawer</span>
                                        <v-radio-group column v-model="primaryDrawer.type">
                                            <v-radio
                                                :key="drawer"
                                                :label="drawer"
                                                :value="drawer.toLowerCase()"
                                                primary
                                                v-for="drawer in drawers"
                                            ></v-radio>
                                        </v-radio-group>
                                        <v-switch
                                            label="Clipped"
                                            primary
                                            v-model="primaryDrawer.clipped"
                                        ></v-switch>
                                        <v-switch
                                            label="Floating"
                                            primary
                                            v-model="primaryDrawer.floating"
                                        ></v-switch>
                                        <v-switch label="Mini" primary v-model="primaryDrawer.mini"></v-switch>
                                    </v-col>
                                    <v-col cols="12" md="6">
                                        <span>Footer</span>
                                        <v-switch label="Inset" primary v-model="footer.inset"></v-switch>
                                    </v-col>
                                </v-row>
                            </v-card-text>
                            <v-card-actions>
                                <v-spacer></v-spacer>
                                <v-btn text>Cancel</v-btn>
                                <v-btn color="primary" text>Submit</v-btn>
                            </v-card-actions>
                        </v-card>
                    </v-col>
                </v-row>
            </v-container>
        </v-main>

        <v-footer :inset="footer.inset" app>
            <span class="px-4">&copy; {{ new Date().getFullYear() }}</span>
        </v-footer>
    </v-app>
</template>

<script>
export default {
    data: () => ({
        drawers: ['Default (no property)', 'Permanent', 'Temporary'],
        primaryDrawer: {
            model: null,
            type: 'default (no property)',
            clipped: false,
            floating: false,
            mini: false,
        },
        footer: {
            inset: false,
        },
    }),
};
</script>