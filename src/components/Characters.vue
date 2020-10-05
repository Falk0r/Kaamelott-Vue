<template>
    <v-container>
        <v-row
            align="center"
            justify="center"
            class="title"
        >
            <v-col
                class="text-center"
                cols="12"
            >
                <h2>Choisissez votre personnage</h2>
            </v-col>
        </v-row>
        <v-row>
            <v-card
                v-for="character in characters" :key="character"
                class="mx-auto"
                max-width="344"
            >
                <v-img
                :src="character.photo"
                height="200px"
                ></v-img>

                <v-card-title>
                    {{character.name}}
                </v-card-title>

                <v-card-subtitle>
                    {{character.actor}}
                </v-card-subtitle>
                <v-card-text>
                    {{character.description}}
                </v-card-text>
                <v-card-actions>
                    <v-btn
                        color="blue lighten-2"
                        text
                        @click="choice(character.name)"
                    >
                        Choisir
                    </v-btn>
                </v-card-actions>
            </v-card>
        </v-row>     
    </v-container>
</template>

<script>
  export default {
    name: 'Characters',
    data: () => ({
        characters: [
            {
                name: "Arthur",
                description: "Arthur Pendragon (dit « le Juste ») est le roi légendaire de l’île de Bretagne et le souverain du royaume de Logres (s’étendant de l'Orcanie à l’Aquitaine), qu’il gouverne dans son château de Kaamelott (Camelot dans les légendes originales). Arthur est le personnage principal de la série.",
                actor: "Alexandre Astier",
                photo: "https://resize.programme-television.ladmedia.fr/rcrop/1200,/img/var/premiere/storage/images/tele-7-jours/news-tv/kaamelott-le-film-le-tournage-a-commence-4632991/95428684-1-fre-FR/Kaamelott-le-film-Le-tournage-a-commence.jpg"
            },
            {
                name: "Léodagan",
                description: "Léodagan (ou Léo De Grand) est, dans la légende arthurienne, généralement le père de Guenièvre et donc le beau-père d'Arthur Pendragon, roi des Bretons. Léodagan est également roi de Carmélide, et gardien de la Table Ronde après la mort d'Uther Pendragon, père et prédécesseur d'Arthur.",
                actor: "Lionnel Astier",
                photo: "https://i.skyrock.net/7673/72107673/pics/2851683178_1.jpg"
            },
            {
                name: "Guenièvre",
                description: "La reine Guenièvre est un personnage de la légende arthurienne, femme du roi Arthur. Sa relation adultère avec Lancelot du Lac est un thème récurrent du cycle. Figure archétypale de la dame courtoise, fée, déesse, Guenièvre est un personnage aux multiples facettes.",
                actor: "Anne Girouard",
                photo: "https://64.media.tumblr.com/386ad52b484ceb981d7c9996e9c45b67/2e049c6efdff9d91-9d/s1280x1920/f8e69b65e3666a175d90c2c3682bd6232dd700f4.png"
            },
            {
                name: "Perceval",
                description: "Perceval de Galles, surnommé Provençal le Gaulois, est un chevalier de la table ronde. De caractère particulièrement niais et stupide, il fait référence, de manière parodique, à son légendaire homonyme, chevalier de la Table ronde originaire de Caerdydd (Cardiff) au Pays de Galles.",
                actor: "Franck Pitiot",
                photo: "data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxISEhUTEhIVFRMVFxUXEhUWFRcVFxUXFRUYFxUXFRYYHSggGBolHRUVITEhJSkrLi4uFx8zODMtNygtLisBCgoKDg0OGhAQGi0dHSUrLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tLS0tNy0tNy0tNy0tLf/AABEIAKgBLAMBIgACEQEDEQH/xAAcAAACAgMBAQAAAAAAAAAAAAADBAIFAAEGBwj/xAA5EAABAwIEBAQEBgIBBAMAAAABAAIRAyEEEjFBBSJRYRNxgZEGocHwByMyQrHRFOHxFVKSomJygv/EABkBAAMBAQEAAAAAAAAAAAAAAAACAwEEBf/EACERAQEAAgMAAgMBAQAAAAAAAAABAhEDITESQSJRYRMy/9oADAMBAAIRAxEAPwDyZpUgUOLLAkOmAtOCjKiZQNmcKLo9YgFAw9lqqSSlvo20Xyi09EuAjAkLaGOdC3hqnMhOWAIGzmOckZTRZIQvBWToUElZCL4CkMOm2AS1RhMf45WGiUbALWkq5wPCXWJGiZ4Jw0fqcPvZXbqPoFPLPXUPMSNDCsFsoHkEz4bdtlPJAsJHzSWJr9FPZ9CVXNaFWPFN5sRK2+XmJQHUAD0T4loWNoGZidJ9oVe8QugoM6z97JLieGIM7J5S2K0iygQiOQy1OUo/VMYbVAqao2H1TQlet/h9eifNdMaXVcv+G7j4bhC64Uzumc+XpYtQ3BNuYgPdtuhmy1bS2qG1si+qMKeUyo1m7hAc7jpD1W8e/SrLiV3qu43S5VP7VjhcZ+pWfDjyeqrcaOZWPDmcnr/SeGyKMaOix1MJbxCpeKoaqu0jSCg/DqXiLRqLQiymZhGNBQDro5qQsta14MKPooHElR8ZGqwU0pUW0QpNepCqEdtFpMWOyBAfXKCTKzQ2Y8Vqyk+TCVcpYYw5boHsUS1McNwxeQSh1hnIXQ8CwRPMbA2HZo1PySW6hpN0/g8NYAfZQMdWAMD78ldUqBAMb/XZKVuHgSTf72Ufk6ccNqeSb838paow7tB/lW1SkNrKIwyaZN/yURgaqIbKuK2BDhceSBTwRaU8pMuOlqTCB92UqjQbHdM4inlGb3QKlwCmRs0o8fhMpVeQujxAzWKo67YKpKSq2pqjYfVBqG6LQKdOvXvwwux4XakC64j8KtHhd5VpxJGqdz5eka5yoDqM826dY3MLhDcIstKUIlLv5ddE7WZuEliHZhA1WVrneKRnskeMjkTuPolr7pTjI5PRT+1Y4DHjmVhw48nqkuIC6ZwLuX1TYmyU9N6MHJZuqYbCSqRNoWNatinOi1EJWseFhFlhMrEBtrFEtW4WwgNjRbChMLJQGFZK0tEoDYCgw3Uy5RbqgLvhtLM9gXonCuHjIzZpme4aWj5kn2XH/DeE/fpaB9SvR8LTa1jGXktAE9Jkk/Jc/Jkvxzso3lc6R0j3gn/1SHEKgmBpsrM3YSNywDqTkkAf+RSH+J11UduvFUVmKAKc4lRII8kiGkJ4KMApERqFKnTUqggGVuwruJ0uU5e/yuqvBiWubuLhXJ3EWg+6qKTYMg9j6KmNc/JC72xY+h+ipca2CVf42wjrcKj4oJIPVVjnyU9UXRKKjXF1ukqpV61+Ez+Zw7Behvb+YZ0XmX4UyapExYL1cUbkEymc2fpWtT3CXc0EJx1jB9EnjTluFuykqlSOXdK1KGW6sPBzCd0EmbFZWuX4w7mCreLvHh+iteN0IcFW8UpDw/RT+1o4DiWq3hakNW+KNuhUTZPiaq5qlKK+lEiNFBrEmzmKcmwRTRe0SWqz4fhhlkap6vUAbBup2mcy5bp3R8RR5raKVOidkfKabJaC6yxqNWoGEBpRLL4NaaeFEoq05tlrAStFSUStY0UfAYcveGtuSYCjSaDqr74XpNbWkXgGPNZbqNk3XRtpCkGtbo0CT1K6rDOJh5JJDST2ABP8hcuw+I865ZEDsD/a7D4VaHHK6+9+ghcmXjqx9VOLrvZStAy99DqY77ei5vFcec113tnuQu94vwltWs2mSWsJkx89V5/8Q8GBxMFoDAMp1MkRz33N7d1uHxvp8vlO4LT4w58ZhI2IRqtYROyq+F8FeKwbRJLSRAOneyuuOYLKXNbsSPZbdS6hpvXbWG4zQiCSD5JjxGPP6rfyuA4jh67STt2TXDq1QsBIdGm4+Sf/AD63CXlu9O0xlIRy3C53FtyHzNlY8Lrk2vpoVvjNIBs/eiWdXTcu5tT4qoC3X/XkqfGjl9U06uLtPdKVaRLbGe335LokcdqpxOqjSKJiwgtVYnXpX4V4kNr3MCPqvWHYtjqnI8E7iV838OrVGmWEg6WXoXwUzEMxDDUzCQdd1sRzx+3qeIcC3vskqDb8yYNEzn2U67MwkaoSI1G5T2S2LZNwng6RBVbiahacqytjm+N4gSJKr8dUBp2QvjwtazXmVZw7iLH0A2RmAgrNfasc1xnVKUnWTnGdUhTNlsOsauGc4ZhEFB/6RVsSLHQqWHxhDQLlNO4zDINypXa1myzXup2JUX4uUjicWXmShh52RqiYnhUMp2lWtYSqinVO6Yw+Kc0wLqeWFppnMTpkyCheBdbFadbHdENSFsmoXLLdRdgjqEtVoOGytW1yNUOtigddUsypsvjf4qFqESrqhlVTaVz8MVw2sJ0NlThM4EkOB3BBHui+Nnr0PDkBx83R5NiB/K634QY3MSNS363XD0Kwc7MCOXX/APQv9912HweYfE2gjzFoXLnOnTj2teNHKcw1C47E0zUcSV2vGDylcVVqwSo4+uvH/mOo4Jw5lGkan7i08x+iqK2DD2ydSZV08luBplxBLo06OuB7JNpGUCQE+MZLLK5/FcEnS6ngeHNbE7Jl+LIcQTcLPETfKs+MHfh2awPZcx8TuhttAVeVMTsqjibA/Kw/udfyRh6zk804OtIMyisMM8/v+07x/Chj8kC1/wCkjhmkhw0tAC65enBnNXSuxSE2ETHNIKWCpJ0kuOF1ch8iCvWsDxloDa+WWNbePmvIKJDW31XQ8B41kYab70z8kbTym3pQ/EXDGxt6FPcL+I6VUwx0rwvi9GHF1O7Srj4D4t4ddocbGx+iYl4+tvZ8bWGrZlKVXCLi6b/y6UAyEpiMfSG4WFmnln4gNeH75VzfCaJcTBOi6H8QeKtqPDW7arm+EY3w3X0KKvj41jXmSDsgMNkzxNwLyRukA+ERtddhsIzw5jZcniWQ4gG0romVT4Nui5dxkqeEWzqbG7qZeJlAWJ9EmWhC6SiirG6jg6GdwHuupwvB2FhkbKXJyY4eq8fHeRzNTEg+ah/kuUa1KHlovBIWm0SSBBuqax0jqnaNSpU2sN0DEvdmhdC1jWUw0agXSdPDy0nLc6KE5Jvxe8fWlawHdShZVOXUJrh+HNU5QPU6ADuqo0ClEhPPqEgQLD5k/YCjW8OmYAzHST9AEfAcTbRF2SDqencI+NZ8osMI99NrXC7nC4ibbeQiF3HwhiocS8wcoP0heaux3MHCTpl/geav+A8XDaoBM8179jaeyly4dLcWfb0/jNWaRhca/CktJJhp9yuir4lpYWz3XJ8Q4iXOyNYXWIbHWwXJhK7MstQbE8QZSpeD+YTMtcDIEC3L8pVcyqahBdWe2P2t09eqU4myqHDNReNOkpWk8tn8t8TYx/K6Mcek95Orq07Agz/KlSdKpcFxISBeZ0II/lXTKoiUmWJ5m08gKi4lxQU3AxJkwJ+afx9W1iuOx2KD6smIFh3I/wCU/HhtLlz0PxGt4pz6l0KTrnoRHrCqxXLHQfT/AEmq2KblnNfy06q+tOW3fZLjrOYEA5e/UmSFXNCPicSah6Dol3FUhKmahTJqENCSCbe38sIoEw+OLTe7dwj4vDZYrUtNbKplWGAxha0sOhWsXNL4nflu4+6BW+InutJ91T4TCl5IkCFGpTDXRMoZ8YsC9r9UliaIBsiYXmIA1JWcRZlcAk3dqQBzZCXKcYFp9ESiZaFi2xNfLRgamy54hXGJo2F/RJeEEY3TcgmYclZQw5c8NNk1TeAm2saYcDcJcs7G44y1r/FFJ1nTKtKvFBSpxq4iyqcY6yS4i648lGYfPW17n8JdHMDicry9wBJRaNcGrNuqq8OZ1UqxuIVLh2nM6sK1aX5SdSrnDMzGG/paLlc9w7BGpUAuBqT2Gq6OliGtqspta0Wc3fMbky7abe0InDvRcub4716qcXUaH3hsG0tzTrcn290FuJLKgfJ1tBsJ19IUuLNyvNgexStJgcACYFgT09FeTSFuxcY8EyNEIOBHUDUaT2lbsQQDMEgHSRsY8lrD7jS/0TFEwlQZCRq0nKNYM29goU21KZa5wI3aZ1g9lNpZo1uUgcxmcxk3A2sQIUaDC3Ucrpa09xcj2Ky4mmT0T4c4q2u0yRnjQm6fwuBddw11Xk+GxD6FUPaY+o6Fen/DHHBWYQ13MP1DpP0XFy8Vw8dvFyy+kuPte4EnNmG40gKpwLKrjBn1CuuLYyHQ6I+qjgMcDYLMd6Vut+gVMMYhw0S1bGljYm4THHOJ5Gm11RYJj67pdYJscbfSZ5zyLXCtdXmP0i5K5TH4FzQ6J5XO+Rg/wvRMA1rKLiNJDW+hlx+S52sA5xDoGcyTe0ncbro48enLy5duUbUaYJF0XEUXOu0XgCBr7botXAfmQwTBMeQm49kekxriJcWweYgZjA7TdUmG0rmU4Tw4vdBt5q0rfDTQf1FL4fFQ7MwkRO1z5jqrLDcWLyA4DzmNOsqfJx8ku8T4Z4a1SmI+Gg2mXhxkKncz8tdrXxjDRcMwmFx5d+U5S48srv5Hyk+ldSp5jC6zgnwTWxNB9amW5aesugkxMALladUAaXVvwz4lr0Kb2U3kNfqFa2/RFfiKRYSJSjlOrWLjJKHK1iTDFxqp1Kma5MlRBERuoEI1tvhllYIvjtSCxZ8INr7jrSyOhVL4hXV/EtPkB6Lk3FLh3D8k1WwTCsOB08ziCq2U7wirlqAdUck/Gs47+UXmM4ZItKq6/DTK6KoSBYqurz1XLhnk6s8Yp/8ACdIgK7w3CRTfFTK4wCCCC2Tt3PZINx5Y7Kxud37idB1A/tPO4g2BnEESbAOiYOuuwXZjP24s8v027GZKgPNlZuIgB14jvBS/FKgbUzAToW3iPJL8QZnIM8pgFw28xr6LK9bMxrp5hY+Y3VZEticQreJzjfXsUkym9sF4PPJaT+68E+63Sc/V05XfpcdJG0+RCzwnvcMoLiATHQC59EN/iGeHAQBbXrfdErOY3LAdnk5iSMpG0D3WPq8hsDMXIki+3QqBcC02kge3dGhsSoGAB0uzl0ERy5Y69ZQaxgh3RTpAPhrnZRIl3TvZSJAJDXZspOV0awbGCt0NtnElvMAD2cJETP0SuFxlSk4PpktI6fweyJQfIIOqnV8NuXKHB1xUmMsWykes/JZcdtlsFxPHqlQy7Xt5RPyU8Lxd4ENBLtzcoLsEHAmIT3C2lrRLS2dDGvkkvHDTkGw9GrVdNQm2yuaT2NGUG37iLmN47qnayqM9U/oDg2ZAvbQb6jRM5XZXVMzQAQIzAOdP/a3U6/Ipbx9nnLqdRaY7ioeAymIYLCVVtIdZ7iMsyWiTYWt7JYFjZcXkVC4BrMphzf8AuzaD/SLiK45QGAG8uBMuJ2O0KsiVpasZE62v36pTD4d8vLBLGjM7YAHQqxqUCwCS0yMwAIJAOgcNiq6qyZbsbtVJ/CffbT4bLoJNoIMAdZEX91jiNRodUX/Ee1jTUAAeCW3BJA3jUKDGNEMaSSdZECToB1W7ZQsSAWxJkT7bX3QsMRkLZ1TpocwbmbP7pMButnEqvZqe3T+t1LPGKY0m4RZalGxDN/dASaOlkMTFlqFYZM1K2yr0BKk0kiE1jWQBa6DhnAXlM4x4IEFJlfyPPCLmwmqWBzAHNqlqj5V7w7FURTAcLjVbbdF6XHGWzSK4uqF2nE3flO8lxLnSk41Ob1oFEw74cD3QltVsSjtmuloPZIYo2TeAM0moFelqvPx9d2Xmy9HDw2dz0+vZV2Lc4Hb76q1YeS0Xmew9ff1SVdoItZu5tM7ldscNV1OoRob79P8AamKouPfzHRQczWLfVRLem2+qeXRbNtudpe06eaZJIFjHlbXVBw9YsOYBpsRDgHC4jQolB0hVnZKzDmyJ4+ZziQBJNgIA7AdFv/Ic4gOP6RAsBaZvGp7lSrVhDWBgFyc15MxY7QI+aNUbBe5uc5W5W2gTO17rfhBoDszeYkFk8wiCCR0M/JMVHUgwhzD4hLcjw6wAnMCIvNvZa/6e6oW5BLjt6ShgVau0BgFMBwLsz5MuBiARpaD7qGIaCAdkZzGENL5gHmyxMbwTZAaczTHp5LZBs3ga0gLWch/7sug1gbwOiWwgcIkEA3aYsR26pnGYl4bkzHwy4OLdswsD7FDfsfE0XPLMgLnbAXJR2MLgGgEv0Ai89ECnWcG5muLXAGC0kEW6hR4fUMSC4OGhBIIPUFGmGamBqPcKbWnxQ4jKbEFtzPoCiNoAnLUeKeUkOcRmALZty63slKDiRBmes385RqWDqAAPaRnByTbMO0+Y91jWxScRnAloAzHYSYEoGIfyEQLEGY5gBOh2F9OwRMXh3U5Y6MzYJgyNLi299FBxmD2TTstJPY4uBaCSdhdFdTF3F2QtBixJLho3stYd7mOhri1zTLXAkEHYgjRRoSQc09Cf9pgkAX3AJMGd9BJPySTiMxvvoR9U6MLUY0FzXBrpDXQQDGsH1Huknnm0lJn4bH0Vmt76WN0tizLiYhMiPIdELFstI138lKxSUBryBAKGtLawzIWLFiAxbDoUViGOw4xVike65Aq84/iNGqjKnx+Kct3WkalTlBUmPI0VLv6JNb7dHgMcWtynZNOxgd5rm6WMINwrPC1muEjyPbe/9Ll/y/J0Xl/E2QMsE2379Alq4kXEN2GvW8opOoi/fbTfrulHPAO7joeg+z/C6HMXqNvLgNoA2USyRNllR5vJva38LTHzqbdP4+vzQxB9ONPVaw5ifNHY4DSbnW+l7JbECDOyfHJlh1/hQ2M3iZjm0y5YER3mUbLTkOqZst5yRMxbXuq7KXERc9EybsgXJiFWJnPCY9vM/KBJzRNwDAt1MD1Q8OMzIPRapUzlc0gg3BBsQR1WYam+mSx4LXDUEQU09Z9BYMS0tKx9Km1+Wm8ubAJJblgkczY7GRKYq41z6jQ6IY0NbAAsOsanuhVaDRL84nMBkgyQQTmB0j+0t/db/CTXkOibbdvJWNR4GV+UPDTdrtCO8KuxrIdKdonM2Fo39pYJ8hFbi3vfzkEtAaIAFmi1h/KHhmta9zWuD2g2dBAI6gG6LXxZljMjQGzzAczpi7jvoFgFrYx9SpzmcoDWwAIb0gevzQ213GoQ4kwABJJgAWAnYdEXHY6fDbkYAAbgQ5x3LjvoEDE4h/K2eSZA/wDl1PXUo1/GmqVF1Jwc+n+W8nLmkB4EEgReL/NRfjg8PPhsbJAgAw2Nct7TF/VK1MQ4vbmJiLAmQI2Cx7WB5DXEy2XyIhx1A6juiRm/0BibEOHkfoiV8dUytp5j4clwbtmOpUC3M2PuRopYSu0CX0w+AeUki+xt06JqyI4iu4luZxIAhoJkNgzA6C6Vy3MayiteC24nWLxB2PdL1Dc+iXPw2PoroH0W+/uhg/czC21TOWrNg9kNOVmyEolpp20sK2VpDWLFixANcSrZqhKVWliJNRlu6xYsWLQ2rjhtPK2e/wB26rFiTO+Gk6o1Q7a9hvvcpLEk7mOw19/UrFi0hc7216/fktgdbe6xYgCgT2+n39FCqSSZjT6/7WLEAAOI0MEI7X21usWK2KeRnCYgmSSSSZJNyfMrVCs59QlxLjOpueyxYmZ+xMS1jXtLXEuIOcERlM2g72goWNaSQQCYEmOgm6xYi9QTutYphc1sXOn9ImBMWOu/nutrFlvY1+LTqRY8H9r5y3H7TBttdHxbqYAJDvEMZSCMoE3kblYsROxeq3i6/wCXGRpJIOczmbGw2gqDsUW08uVsOiXES4RflO23ssWIEqGLxDoYJGUEkCBrHXdQqA5wdjAW1iN6bOxGNAcW5gZv/wDWTofvdBqsyu1BBnTtqfJYsWy1mkatEMsHh0ibftJ/ae6VtPX/AIWLEufhsfUp7W8tPuywfdlixTPU2FK1BdYsRREVi0sSnbW4WLEB/9k="
            },
            {
                name: "Karadoc",
                description: "Karadoc de Vannes est, comme Perceval , un chevalier d’extraction modeste anobli par le Roi Arthur (L’Approbation). Il est le meilleur ami de Perceval et est aussi incompétent que lui en ce qui concerne les quêtes et les combats. Le duo tente régulièrement de mener à bien des missions, qui sont en général des échecs",
                actor: "Jean-Christophe Hembert",
                photo: "https://memegenerator.net/img/images/72402366.jpg"
            },
        ]
    }),
    props : ['choice'],
  }
</script>
