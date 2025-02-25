# Abir-Book
social media Apps
function checkLogin() {
    let user = localStorage.getItem("user");
    if (!user) {
        window.location.href = "login.html";
    }
}

function login() {
    let emailOrPhone = document.getElementById("emailOrPhone").value;
    let password = document.getElementById("password").value;

    let user = localStorage.getItem(emailOrPhone);
    if (user) {
        let userData = JSON.parse(user);
        if (userData.password === password) {
            localStorage.setItem("user", JSON.stringify(userData));
            window.location.href = "index.html";
        } else {
            alert("Incorrect password!");
        }
    } else {
        alert("User not found! Please sign up.");
    }
}

function signup() {
    let name = document.getElementById("signupName").value;
    let emailOrPhone = document.getElementById("signupEmail").value;
    let password = document.getElementById("signupPassword").value;

    let user = { name, emailOrPhone, password, profilePic: "default-profile.png" };
    localStorage.setItem(emailOrPhone, JSON.stringify(user));

    alert("Account created! Now login.");
}

function logout() {
    localStorage.removeItem("user");
    window.location.href = "login.html";
}
