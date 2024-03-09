<h1>Обо мне</h1>
<p>Люблю поспать</p>

<script>
    import video1 from './sleep.mp4';
</script>

<video width="500" height="400" autoplay loop muted>
<source src={video1} type='video/mp4; codecs="avc1.42E01E, mp4a.40.2"'>
</video>

<style>

:root {
    --primary-color: #3498db;
}
    video {
  margin-left: -100px; 
}
h1, h2 {
    color: var(--primary-color);
}
</style>
