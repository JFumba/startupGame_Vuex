<template>
    <div class="overview">
        <h3>Current Bytes</h3>
        <div class="bytes">{{ bytes }}</div>
        <div class="bps">Bytes per Second: {{ bps }}</div>
        <div class="level">Current Level: {{ level }}</div>
        <div class="next-level">Bytes Until next Level: {{ bytesUntilLevelUp }}</div>
    </div>
</template>

<script>
export default {
    name: 'overview',
    computed: {
        bytes () {
            return Math.round(this.$store.state.bytes);
        },
        bps () {
            return (this.$store.state.bps).toFixed(1);
        },
        level () {
            return this.$store.state.player.level;
        },
        bytesUntilLevelUp () {
            return this.$store.getters.bytesUntilLevelUp;
        }
    }
}
</script>