//template Password Check
let passwordTemplateCheck = {
    template: "#password-check-template",

    data(){
        return {
            password: '',
            path: 'hello',
            background: null,
            'imageAlt': null,
            title: null,
            subtitle: null,
        }
    },

    computed: {
        // functions to verify if the password has the demands
        lineClass(){
            let className = 'default';
                if(this.password.length > 7){
                    className = 'line';
                }
            return className;
        },
        hasLowerCase(str) {
            let className = 'default';
            if(/[a-z]/.test(str.password)){
                className = 'line';
            }else {
                className = 'default';
            }
            return className;
        },
        hasUpperCase(str) {
            let className = 'default';
            if(/[A-Z]/.test(str.password)){
                className = 'line';
            }else {
                className = 'default';
            }
            return className;
        },
        hasNumbers(str){
            let className = 'default';
            if(/\d/.test(str.password)){
                className = 'line';
            }else {
                className = 'default';
            }
            return className;
        },
        hasSpecialCharacters(str){
            let className = 'default';
            if(/\W/g.test(str.password)){
                className = 'line';
            }else {
                className = 'default';
            }
            return className;
        },
        hasNoSpaces(str){
            let className = 'default';
            if(str.password.indexOf(' ') >= 0){
                className = 'colorRed';
            }else {
                className = 'default';
            }            
            return className;
        },
        
    },

    methods: {
        choseLocale(chosen){

            // send information to variable with the correct locale
            //background
            this.background = this.$i18n.messages[chosen].background;

            //for image-alt
            this.imageAlt = this.$i18n.messages[chosen].imageFrom;

            //send title
            this.title = this.$i18n.messages[chosen].title;

            //send subtitle
            this.subtitle = this.$i18n.messages[chosen].password;
            // return the correct locale
            return chosen        
        },
    },
    
};

new Vue({
    el:"#app",

    components: {
        'password-check-template': passwordTemplateCheck
    },

    data(){
        return {
            fr: 'fr',
            en:'en',
            language: null,
            langs: ['en', 'fr', 'es'],
        }
    },

    i18n: new VueI18n({
        fallbackLocale: 'en',
        messages,
    }),

});


