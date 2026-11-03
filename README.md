<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Atul AI Studio | Wallpapers & Photos</title>

<style>
*{box-sizing:border-box;margin:0;padding:0}
body{
  font-family:Arial,sans-serif;
  background:#0b0b0f;color:#fff;
}
header{
  padding:20px 6%;
  display:flex;justify-content:space-between;
  align-items:center;gap:15px;
  background:#15151c;border-bottom:1px solid #292933;
}
.logo{font-size:23px;font-weight:bold;color:#a78bfa}
nav{display:flex;gap:12px;flex-wrap:wrap}
button{
  border:0;padding:10px 15px;border-radius:8px;
  background:#272731;color:white;cursor:pointer;
}
button:hover{background:#7655e8}
.primary{background:#7655e8}
.container{padding:25px 6%}
.hero{
  padding:50px 20px;text-align:center;
  background:linear-gradient(135deg,#242035,#11121a);
  border-radius:18px;margin-bottom:30px;
}
.hero h1{font-size:35px;margin-bottom:12px}
.hero p{color:#c4c4d0;margin-bottom:20px}
.tabs{display:flex;gap:10px;margin:25px 0;flex-wrap:wrap}
.tabs button.active{background:#7655e8}
.grid{
  display:grid;
  grid-template-columns:repeat(auto-fill,minmax(220px,1fr));
  gap:20px;
}
.card{
  background:#17171f;border:1px solid #292933;
  border-radius:14px;overflow:hidden;
}
.card img{
  width:100%;height:240px;object-fit:cover;
  display:block;
}
.card-content{padding:15px}
.card h3{margin-bottom:10px}
.card p{color:#aaa;font-size:13px;margin-bottom:12px}
.actions{display:flex;gap:8px;flex-wrap:wrap}
.actions button{font-size:12px;padding:9px}
section{margin-bottom:35px}
h2{margin-bottom:18px}
footer{
  padding:30px 6%;background:#15151c;
  color:#aaa;text-align:center;line-height:2;
}
input,textarea,select{
  width:100%;padding:12px;margin:8px 0;
  border-radius:8px;border:1px solid #333;
  background:#101016;color:white;
}
label{display:block;margin-top:12px}
.panel{
  background:#17171f;padding:20px;
  border-radius:14px;margin-bottom:20px;
}
.hidden{display:none!important}
#editor img{
  max-width:100%;max-height:400px;
  object-fit:contain;
}
.notice{font-size:13px;color:#aaa;margin-top:10px}
@media(max-width:600px){
  header{flex-direction:column}
  .hero h1{font-size:27px}
  .container{padding:18px 4%}
}
</style>
</head>

<body>

<header>
  <div class="logo">ATUL AI STUDIO</div>
  <nav>
    <button onclick="showPage('home')">Home</button>
    <button onclick="showPage('editor')">Editor</button>
    <button onclick="showPage('admin')">Admin</button>
  </nav>
</header>

<main class="container">

<!-- HOME -->
<div id="home">

  <div class="hero">
    <h1 id="siteTitle">Discover Beautiful Wallpapers</h1>
    <p id="siteSubtitle">
      Premium wallpapers, creative photos and personal editing.
    </p>
    <button class="primary" onclick="document.getElementById('gallery').scrollIntoView()">
      Explore Photos
    </button>
  </div>

  <div class="tabs">
    <button id="freeTab" class="active" onclick="setTab('free')">
      Free Photos
    </button>
    <button id="sellTab" onclick="setTab('sell')">
      Selling
    </button>
  </div>

  <section id="gallery">
    <h2 id="galleryTitle">Free Wallpapers</h2>
    <div id="photoGrid" class="grid"></div>
  </section>

</div>

<!-- EDITOR -->
<div id="editor" class="hidden">
  <h2>Personal Photo Editor</h2>

  <div class="panel">
    <label>Select your photo</label>
    <input type="file" id="editFile" accept="image/*">

    <div style="text-align:center;margin:15px">
      <img id="editPreview" alt="Photo preview">
    </div>

    <label>Brightness</label>
    <input type="range" id="brightness" min="50" max="150" value="100">

    <label>Contrast</label>
    <input type="range" id="contrast" min="50" max="150" value="100">

    <label>Saturation</label>
    <input type="range" id="saturation" min="0" max="200" value="100">

    <label>Wallpaper size</label>
    <select id="wallpaperSize">
      <option value="1080,1920">Mobile Wallpaper</option>
      <option value="1920,1080">Desktop Wallpaper</option>
      <option value="1080,1080">Square Wallpaper</option>
    </select>

    <button onclick="resetEditor()">Reset</button>
    <button class="primary" onclick="downloadEdited()">Download Edited Photo</button>
  </div>
</div>

<!-- ADMIN -->
<div id="admin" class="hidden">

  <h2>Admin Dashboard</h2>

  <div id="loginBox" class="panel">
    <h3>Admin Login</h3>

    <input id="adminID" placeholder="Admin ID">
    <input id="adminPassword" type="password" placeholder="Admin Password">

    <button class="primary" onclick="login()">Login</button>

    <p class="notice">
      Demo login is configured in the JavaScript below.
      For production, use secure server-side authentication.
    </p>
  </div>

  <div id="adminPanel" class="hidden">

    <div class="panel">
      <h3>Website Settings</h3>

      <label>Website Title</label>
      <input id="newTitle">

      <label>Homepage Subtitle</label>
      <input id="newSubtitle">

      <label>Instagram ID</label>
      <input id="instagram">

      <label>Contact Email</label>
      <input id="contact">

      <button class="primary" onclick="saveSettings()">Save Settings</button>
    </div>

    <div class="panel">
      <h3>Upload Photo</h3>

      <label>Photo</label>
      <input type="file" id="uploadFile" accept="image/*">

      <label>Photo Title</label>
      <input id="photoTitle" placeholder="Enter photo title">

      <label>Category</label>
      <select id="photoCategory">
        <option value="free">Free</option>
        <option value="sell">Selling</option>
      </select>

      <label>Price (₹)</label>
      <input type="number" id="photoPrice" min="0" value="0">

      <button class="primary" onclick="uploadPhoto()">Upload Photo</button>
    </div>

    <div class="panel">
      <h3>Manage Photos</h3>
      <div id="managePhotos"></div>
    </div>

    <button onclick="logout()">Logout</button>

  </div>
</div>

</main>

<footer>
  <h3 id="footerTitle">Atul AI Studio</h3>
  <p>Creative wallpapers and photography</p>
  <p id="footerInstagram">Instagram: Not added</p>
  <p id="footerContact">Contact: Not added</p>
  <p>© 2026 Atul AI Studio</p>
</footer>

<script>

// ==========================================
// DEMO ADMIN LOGIN
// ==========================================
// IMPORTANT:
// These credentials are visible in frontend source.
// Do not use this authentication for a public
// production website.
//
// Replace with secure backend authentication
// before publishing the real website.

const DEMO_ADMIN_ID = "CHANGE_ADMIN_ID";
const DEMO_ADMIN_PASSWORD = "CHANGE_ADMIN_PASSWORD";

// ==========================================

let photos = [];
let settings = {
  title:"Discover Beautiful Wallpapers",
  subtitle:"Premium wallpapers, creative photos and personal editing.",
  instagram:"",
  contact:""
};

let currentTab = "free";
let isAdmin = false;
let editingPhoto = null;
let editImage = new Image();

// Local demo storage.
// Production: use database + private file storage.

try {
  photos = JSON.parse(localStorage.getItem("atulPhotos") || "[]");
  settings = JSON.parse(localStorage.getItem("atulSettings")) || settings;
} catch(e) {
  photos=[];
}

function saveData(){
  try{
    localStorage.setItem("atulPhotos",JSON.stringify(photos));
    localStorage.setItem("atulSettings",JSON.stringify(settings));
  }catch(e){
    alert("Storage full. Use server storage for large photos.");
  }
}

function showPage(page){
  ["home","editor","admin"].forEach(id=>{
    document.getElementById(id).classList.add("hidden");
  });

  document.getElementById(page).classList.remove("hidden");

  if(page==="admin") updateAdmin();
}

function setTab(tab){
  currentTab=tab;

  document.getElementById("freeTab").classList.toggle("active",tab==="free");
  document.getElementById("sellTab").classList.toggle("active",tab==="sell");

  document.getElementById("galleryTitle").textContent=
    tab==="free"?"Free Wallpapers":"Selling";

  renderPhotos();
}

function renderPhotos(){
  const grid=document.getElementById("photoGrid");
  grid.innerHTML="";

  const filtered=photos.filter(p=>p.category===currentTab);

  if(filtered.length===0){
    grid.innerHTML="<p>No photos available yet.</p>";
    return;
  }

  filtered.forEach(photo=>{
    const card=document.createElement("article");
    card.className="card";

    const img=document.createElement("img");
    img.src=photo.image;
    img.alt=photo.title;

    const content=document.createElement("div");
    content.className="card-content";

    const title=document.createElement("h3");
    title.textContent=photo.title;

    const desc=document.createElement("p");
    desc.textContent=photo.category==="free"
      ?"Free Wallpaper"
      :"Price: ₹"+photo.price;

    const actions=document.createElement("div");
    actions.className="actions";

    const download=document.createElement("button");
    download.textContent="Download";
    download.onclick=()=>downloadPhoto(photo);

    const edit=document.createElement("button");
    edit.textContent="Edit";
    edit.onclick=()=>openEditor(photo);

    actions.append(download,edit);
    content.append(title,desc,actions);

    card.append(img,content);
    grid.append(card);
  });
}

function downloadPhoto(photo){
  if(photo.category==="sell"){
    alert("This photo is in the Selling section. Payment checkout is not connected yet.");
    return;
  }

  const a=document.createElement("a");
  a.href=photo.image;
  a.download=photo.title+".jpg";
  a.click();
}

function login(){
  const id=document.getElementById("adminID").value;
  const password=document.getElementById("adminPassword").value;

  if(id===DEMO_ADMIN_ID && password===DEMO_ADMIN_PASSWORD){
    isAdmin=true;
    document.getElementById("loginBox").classList.add("hidden");
    document.getElementById("adminPanel").classList.remove("hidden");
    updateAdmin();
  }else{
    alert("Incorrect Admin ID or Password");
  }
}

function logout(){
  isAdmin=false;
  document.getElementById("loginBox").classList.remove("hidden");
  document.getElementById("adminPanel").classList.add("hidden");
}

function updateAdmin(){
  if(!isAdmin)return;

  document.getElementById("newTitle").value=settings.title;
  document.getElementById("newSubtitle").value=settings.subtitle;
  document.getElementById("instagram").value=settings.instagram;
  document.getElementById("contact").value=settings.contact;

  const box=document.getElementById("managePhotos");
  box.innerHTML="";

  photos.forEach(photo=>{
    const row=document.createElement("div");
    row.className="panel";

    const name=document.createElement("p");
    name.textContent=photo.title+" ("+photo.category+")";

    const del=document.createElement("button");
    del.textContent="Delete";
    del.onclick=()=>deletePhoto(photo.id);

    row.append(name,del);
    box.append(row);
  });
}

function saveSettings(){
  if(!isAdmin)return;

  settings.title=document.getElementById("newTitle").value;
  settings.subtitle=document.getElementById("newSubtitle").value;
  settings.instagram=document.getElementById("instagram").value;
  settings.contact=document.getElementById("contact").value;

  saveData();
  applySettings();

  alert("Settings saved!");
}

function applySettings(){
  document.getElementById("siteTitle").textContent=settings.title;
  document.getElementById("siteSubtitle").textContent=settings.subtitle;
  document.getElementById("footerTitle").textContent=settings.title;

  document.getElementById("footerInstagram").textContent=
    "Instagram: "+(settings.instagram||"Not added");

  document.getElementById("footerContact").textContent=
    "Contact: "+(settings.contact||"Not added");
}

function uploadPhoto(){
  if(!isAdmin){
    alert("Admin login required");
    return;
  }

  const file=document.getElementById("uploadFile").files[0];
  const title=document.getElementById("photoTitle").value.trim();
  const category=document.getElementById("photoCategory").value;
  const price=Number(document.getElementById("photoPrice").value);

  if(!file || !title){
    alert("Select a photo and enter its title");
    return;
  }

  if(file.size>3*1024*1024){
    alert("Demo supports photos up to 3 MB. Use backend storage for larger photos.");
    return;
  }

  const reader=new FileReader();

  reader.onload=()=>{
    photos.push({
      id:Date.now(),
      title:title,
      category:category,
      price:category==="sell"?price:0,
      image:reader.result
    });

    saveData();
    renderPhotos();
    updateAdmin();

    document.getElementById("uploadFile").value="";
    document.getElementById("photoTitle").value="";

    alert("Photo uploaded!");
  };

  reader.readAsDataURL(file);
}

function deletePhoto(id){
  if(!isAdmin)return;

  if(confirm("Delete this photo?")){
    photos=photos.filter(p=>p.id!==id);
    saveData();
    renderPhotos();
    updateAdmin();
  }
}

// ==========================================
// PHOTO EDITOR
// ==========================================

document.getElementById("editFile").addEventListener("change",e=>{
  const file=e.target.files[0];
  if(!file)return;

  const reader=new FileReader();

  reader.onload=()=>{
    editImage=new Image();

    editImage.onload=()=>{
      document.getElementById("editPreview").src=reader.result;
      resetEditor();
    };

    editImage.src=reader.result;
  };

  reader.readAsDataURL(file);
});

function openEditor(photo){
  showPage("editor");

  editingPhoto=photo;
  document.getElementById("editPreview").src=photo.image;

  editImage=new Image();
  editImage.onload=resetEditor;
  editImage.src=photo.image;
}

function resetEditor(){
  ["brightness","contrast","saturation"].forEach(id=>{
    document.getElementById(id).value=100;
  });

  applyFilters();
}

["brightness","contrast","saturation"].forEach(id=>{
  document.getElementById(id).addEventListener("input",applyFilters);
});

function applyFilters(){
  const b=document.getElementById("brightness").value;
  const c=document.getElementById("contrast").value;
  const s=document.getElementById("saturation").value;

  document.getElementById("editPreview").style.filter=
    `brightness(${b}%) contrast(${c}%) saturate(${s}%)`;
}

function downloadEdited(){
  if(!editImage.src){
    alert("Select a photo first");
    return;
  }

  const size=document.getElementById("wallpaperSize").value.split(",");
  const width=Number(size[0]);
  const height=Number(size[1]);

  const canvas=document.createElement("canvas");
  canvas.width=width;
  canvas.height=height;

  const ctx=canvas.getContext("2d");

  const b=document.getElementById("brightness").value;
  const c=document.getElementById("contrast").value;
  const s=document.getElementById("saturation").value;

  ctx.filter=`brightness(${b}%) contrast(${c}%) saturate(${s}%)`;

  // Fit photo inside selected wallpaper dimensions.
  const scale=Math.min(width/editImage.width,height/editImage.height);
  const w=editImage.width*scale;
  const h=editImage.height*scale;

  ctx.fillStyle="#101016";
  ctx.fillRect(0,0,width,height);

  ctx.drawImage(editImage,(width-w)/2,(height-h)/2,w,h);

  const a=document.createElement("a");
  a.download="atul-wallpaper.jpg";
  a.href=canvas.toDataURL("image/jpeg",0.95);
  a.click();
}

// ==========================================

applySettings();
renderPhotos();

</script>
</body>
</html>
create table public.photos (
  id bigint generated always as identity primary key,
  title text not null,
  image_url text not null,
  category text not null default 'free'
    check (category in ('free', 'sell')),
  price numeric default 0,
  created_at timestamptz default now()
);

create table public.site_settings (
  id integer primary key default 1,
  title text default 'Atul AI Studio',
  subtitle text default 'Creative Wallpapers',
  instagram text default '',
  contact text default ''
);
