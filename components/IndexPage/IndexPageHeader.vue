<template>
    <header class="main-header page-wrapper medium">
        <PageTitle :title="index.header_title" :description="index.header_description" />

        <div v-if="!config.isAuthenticated">
            <!--User registration button-->
            <router-link v-if="config.userRegistration" class="sign-up-button" :to="{ name: 'SignUp' }">
                <AuthButton class="button" icon="chevron-right" :text="$t('page_index.sign_up_button')" />
            </router-link>

            <!--User login button-->
            <router-link v-if="!config.userRegistration" class="sign-up-button" :to="{ name: 'SignIn' }">
                <AuthButton class="button" icon="chevron-right" :text="$t('log_in')" />
            </router-link>

    </header>
</template>

<script>
import PageTitle from './Components/PageTitle'
import AuthButton from '../UI/Buttons/AuthButton'
import { mapGetters } from 'vuex'

export default {
    name: 'IndexPageHeader',
    components: {
        PageTitle,
        AuthButton,
    },
    computed: {
        ...mapGetters(['index', 'config']),
    },
}
</script>

<style lang="scss" scoped>

.features {
    display: flex;
    margin-top: 35px;

    .feature {
        display: flex;
        margin-right: 35px;

        &:nth-child(1) {
            path,
            line,
            polyline,
            rect,
            circle {
                stroke: $yellow;
            }
        }

        &:nth-child(2) {
            path,
            line,
            polyline,
            rect,
            circle {
                stroke: $purple;
            }
        }

        &:last-child {
            margin-right: 0;
        }

        .feature-title {
            @include font-size(14);
            font-weight: 700;
        }

        .feature-icon {
            margin-right: 10px;
        }
    }
}

.main-header {
    padding-top: 70px;
}

.sign-up-button {
    margin-top: 65px;
    display: block;

    .button {
        margin-left: 0;
        margin-right: 0;
    }
}

@media only screen and (max-width: 690px) {
    .main-header {
        padding-top: 50px;
    }

    .features {
        display: block;

        .feature {
            margin-right: 0;
            margin-bottom: 15px;

            &:last-child {
                margin-bottom: 0;
            }
        }
    }

    .sign-up-button {
        margin-top: 30px;
    }
}
</style>
