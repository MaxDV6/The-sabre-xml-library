# The-sabre-xml-library
Major version 3 implements type declarations for input parameters, function returns, variables etc.
<?php
$Name  = $_POST['Name'];
$Email = $_POST['Email'];
$Major = $_POST['Major'];

$xml = new DOMDocument();

// Check if XML loads correctly
if (!$xml->load('data.xml')) {
    die('Error loading XML file');
}

$root = $xml->getElementsByTagName('trainees')->item(0);

if ($root === null) {
    die('Root <trainees> not found');
}

// Create trainee
$trainee = $xml->createElement('trainee');
$trainee->appendChild($xml->createElement('Name', $Name));
$trainee->appendChild($xml->createElement('Email', $Email));
$trainee->appendChild($xml->createElement('Major', $Major));

// Append and save
$root->appendChild($trainee);
$xml->save('data.xml');
?>
