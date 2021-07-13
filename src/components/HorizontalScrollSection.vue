<template>
    <section class="horizontal-section">
        <div class="sticky-wrapper">
            <div class="element-wrapper">
                <slot></slot>
            </div>
        </div>
    </section>
</template>
<script>
export default {
    name: 'HorizontalScrollSection',

    mounted() {
        this.init()
    },

    methods: {
        init() {
            let windowWidth = this.calcWindowWidth();
            let horizontalLength = this.$el.querySelector( '.element-wrapper' ).scrollWidth;
            let distFromTop = this.$el.offsetTop;
            let scrollDistance = this.calcScrollDistance( distFromTop, horizontalLength, windowWidth );

            this.$el.style.height = horizontalLength + "px";

            window.onresize = () => { 
                windowWidth = this.calcWindowWidth();
                scrollDistance = this.calcScrollDistance( distFromTop, horizontalLength, windowWidth );
            }

            window.onscroll = () => {
                let scrollTop = window.pageYOffset;

                if ( scrollTop >= distFromTop && scrollTop <= scrollDistance ) {
                    document.querySelector( '.element-wrapper' ).style.transform = "translateX(-" + ( scrollTop - distFromTop ) + "px)";
                }
            }
        },

        calcWindowWidth() {
            return window.innerWidth;
        },

        calcScrollDistance( distFromTop, horizontalLength, windowWidth ) {
            return distFromTop + horizontalLength - windowWidth;
        }
    }
}
</script>
<style lang="scss" scoped>
.horizontal-section {
    padding: 10rem 0;
    background-color: indigo;

    .sticky-wrapper {
        width: 100%;
        overflow: hidden;
        position: sticky;
        top: 10rem;
    }

    .element-wrapper {
        position: relative;
        display: flex;

        & > * {
            flex-shrink: 0; /* prevents elements from shrinking in width to stay contained in the flexbox */
        }
    }
}
</style>
