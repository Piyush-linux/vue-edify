<template>
    <div class="column is-1 has-text-centered" :class="{ sidebarDark: dark , sidebarLight: !dark}">
        <!-- mode -->
        <div class="field" data-tooltip="Toggle Light Mode">
            <label class="switch is-rounded btn">
                <input type="checkbox" value="false" checked @click="toggleMode">
                <span class="check"></span>
            </label>
        </div>
        <!-- clear -->
        <div class="field">
            <div class="button is-medium btn is-rounded is-light" @click="txtClear">
                <span class="icon is-medium">
                    <span class="iconify" data-icon="akar-icons:comment-add"></span>
                </span>
            </div>
        </div>
        <!-- capital -->
        <div class="field">
            <div class="button is-medium btn is-rounded is-light" @click="txtUpp">
                <span class="icon is-medium">
                    <span class="iconify" data-icon="radix-icons:letter-case-uppercase"></span>
                </span>
            </div>
        </div>
        <!-- LowCase -->
        <div class="field">
            <div class="button is-medium btn is-rounded is-light" @click="txtLow">
                <span class="icon is-medium">
                    <span class="iconify" data-icon="tabler:letter-case-lower"></span>
                </span>
            </div>
        </div>
        <!-- copy -->
        <div class="field">
            <div class="button is-medium btn is-rounded is-light" @click="txtCpy">
                <span class="icon is-medium">
                    <span class="iconify" data-icon="fluent:copy-16-filled"></span>
                </span>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: "Textarea",
    props:["dark","toggleMode","txtClear","txtCpy","txtUpp"],
    methods:{
    	
    }

}
</script>
<style></style>