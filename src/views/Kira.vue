<template>
        <div>
            <Main/>
        </div>
</template>
<script>
import Main from '@/Kira/Main.vue';
export default{
    name: 'Kira',
    components: {
       Main,
    },
    mounted() {
     const scriptPaths = [
       '/kira/js/login.js',
   
        ];

        const loadScript = (path) => {
        return new Promise((resolve, reject) => {
            const script = document.createElement('script');
            script.src = path;
            script.onload = resolve;
            script.onerror = reject;
            document.body.appendChild(script);
        });
        };

        const loadScripts = async () => {
        try {
            await loadScript(scriptPaths[0]); // Load jQuery first
            for (let i = 1; i < scriptPaths.length; i++) {
            await loadScript(scriptPaths[i]);
            }
        } catch (error) {
            console.error('Failed to load scripts:', error);
        }
        };
        loadScripts();
    }
}
</script>
<style>

</style>
