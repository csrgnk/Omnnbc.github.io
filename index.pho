<?php
// Path to posts folder
$postsDir = '_posts/';

// Get all files in descending order (newest first)
$files = array_diff(scandir($postsDir, SCANDIR_SORT_DESCENDING), array('..', '.'));

// Start HTML
echo "<!DOCTYPE html>
<html>
<head>
<meta charset='utf-8'>
<title>Omnnbc Blog</title>
<style>
body { font-family: Arial; max-width: 720px; margin: 40px auto; padding: 0 10px; }
h1 { color: #222; }
a { text-decoration: none; color: #0073aa; }
a:hover { text-decoration: underline; }
.post-date { font-size: 12px; color: #777; }
ul { list-style: none; padding-left: 0; }
li { margin-bottom: 20px; }
</style>
</head>
<body>
<h1>Omnnbc Blog Posts</h1>
<ul>";

// Loop through each file
foreach($files as $file){
    if(pathinfo($file, PATHINFO_EXTENSION) === 'md'){

        // Read file contents
        $content = file_get_contents($postsDir.$file);

        // Extract title from front-matter
        preg_match('/title:\s*(.+)/', $content, $titleMatch);
        $title = $titleMatch[1] ?? 'Untitled';

        // Extract date
        preg_match('/date:\s*(.+)/', $content, $dateMatch);
        $date = $dateMatch[1] ?? '';

        // Generate slug for URL (remove date prefix)
        $slug = preg_replace('/^\d+\./', '', pathinfo($file, PATHINFO_FILENAME));

        // Output list item
        echo "<li><a href='$slug/'>{$title}</a><br><span class='post-date'>{$date}</span></li>";
    }
}

echo "</ul>
</body>
</html>";
?>
