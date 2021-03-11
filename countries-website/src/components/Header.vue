<template>
    <header>
        <h1> Where In The World?</h1>
        <nav>
            <Toggle :mode="mode" @toggle="$emit('toggle')"/>
        </nav>
    </header>
</template>

<script>
import Toggle from '@/components/Toggle'
export default {
    props: ['mode'],
    components: {
        Toggle
    }
}

</script>

<style scoped>

.dark header {
    background: #15202B;
}

header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 25px;
    height: 60px;
    background: hsl(0, 0%, 100%);
    transition: background 0.3 ease-in-out;
}

header h1 {
    font-size: 24px;
    font-weight: 900;
}

header nav {
    display: flex;
}

header nav .nav-link {
    align-items: center;
    padding: 0px 15px;
}
</style>