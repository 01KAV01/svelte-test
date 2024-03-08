<script>
    export let name;
    export let icon; // Добавлено экспортирование переменной icon

    const icons = [
        {
            name: 'check-mark',
            path: '/src/components/check-mark.jpg',
        },
        {
            name: 'delete',
            path: '/src/components/delete.svg', // Предполагается, что у вас есть SVG файл для delete
        }
    ];

    icon = icons.find((item) => item.name === name); // Используем строгое сравнение
</script>
