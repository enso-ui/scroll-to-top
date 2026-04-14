<template>
    <core-scroll-to-top>
        <template #default="{ visible, type, controlEvents }">
            <zoom>
                <button class="button scroll-control"
                    :class="[type, $attrs.class]"
                    type="button"
                    v-on="controlEvents"
                    v-if="visible">
                    <slot>
                        <span class="icon">
                            <fa :icon="faCircleUp"/>
                        </span>
                    </slot>
                </button>
            </zoom>
        </template>
    </core-scroll-to-top>
</template>

<script>
import { Zoom } from '@enso-ui/transitions';
import { FontAwesomeIcon as Fa } from '@fortawesome/vue-fontawesome';
import { faCircleUp } from '@fortawesome/free-solid-svg-icons';
import CoreScrollToTop from '../renderless/CoreScrollToTop.vue';

export default {
    name: 'ScrollToTop',

    components: { CoreScrollToTop, Fa, Zoom },

    data: () => ({
        faCircleUp,
    }),
};
</script>

<style lang="scss">
    .button.scroll-control {
        z-index: 41;
        position: fixed;
        bottom: 2.5em;

        @media screen and (min-width: 769px) {
            [dir='ltr'] & {
                left: auto;
                right: 1.5em;
            }
            [dir='rtl'] & {
                right: auto;
                left: 1.5em;
            }
        }
        @media screen and (max-width: 768px) {
            [dir='ltr'] & {
                left: auto;
                right: 0.5em;
            }
            [dir='rtl'] & {
                right: auto;
                left: 0.5em;
            }
        }
    }

    [data-theme='light'] {
        .button.scroll-control {
            color: #fff;

            &:hover,
            &:focus,
            &:active,
            &.is-hovered,
            &.is-focused,
            &.is-active {
                color: #fff;
            }
        }
    }

</style>
