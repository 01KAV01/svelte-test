<script>
    export let name;
    export let icon; 

    const icons = [
        {
            name: 'check-mark',
            path: '/src/components/check-mark.jpg',
        },
        {
            name: 'delete',
            path: '/src/components/delete.jpg', 
        }
    ];

    icon = icons.find((item) => item.name === name); 
</script>
