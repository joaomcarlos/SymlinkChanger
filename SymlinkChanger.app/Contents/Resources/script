<?php

function create_symlink($from, $to){
  // from some project files
  // to htdocs folder in Mamp
  return shell_exec('ln -s "'.$from.'" "'.$to.'"');
}
function doGui($command){
  $CD="CocoaDialog.app/Contents/MacOS/CocoaDialog";
  return shell_exec($CD." ".$command);
}

$pathToMamp = "/Applications/MAMP";
$projects = array(
  array("name"=>"P1WebForm", "loc"=>"/Users/silent/Documents/Dropbox/Development/anders/P1-webform"),
  array("name"=>"Mafia", "loc"=>"/Users/silent/Documents/Dropbox/Development/WebSites/Trabalhos/Mafia")
);

$code  = ' dropdown';
$code .= ' --title "Preferred Project"';
$code .= ' --no-newline';
$code .= ' --text "What project do you want to work on?"';
$code .= ' --items ';
foreach($projects as $project){
  $code .= '"'.$project["name"].'" ';
}
$code .= ' --button1 "That one!"';
$code .= ' --button2 Nevermind';

$ret = explode("\n",doGui($code));
$button = $ret[0];
$item = $ret[1];

if($button == 1){
  $project = $projects[$item];
  // delete htdocs, will fail if its directory and thats good
  shell_exec('rm '.$pathToMamp.'/htdocs');
  create_symlink($project[loc], $pathToMamp.'/htdocs');
  doGui('ok-msgbox --no-cancel --text "Changed to "'.$project["name"]);
}

die();
