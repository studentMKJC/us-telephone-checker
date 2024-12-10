# us-telephone-checker
a code that checks for validity of a us phone number
const result = document.getElementById("result-div");
const buttons = document.getElementsByClassName("dial-btn");
const input = document.getElementById("user-input");
const check = document.getElementById("check-btn");
const clear = document.getElementById("clear-btn");

// Function to check if the phone number is valid using regex
const checkNumber = (str) => {
    const regex = /^[1]?\(?5{3}\)?[-\s]?5{3}[-\s]?5{4}$/;
    return regex.test(str); 
}


const handleButtonClick = (event) => {
    const value = event.target.getAttribute('data-value');
    input.value += value;
}


const validatePhoneNumber = () => {
    const phoneNumber = input.value;

    
    if (phoneNumber.trim() === "") {
        alert("Please enter a number.");
        return;
    }

    
    const isValid = checkNumber(phoneNumber);

    if (isValid) {
        result.textContent = `Valid US number: ${phoneNumber}`;
        result.style.color = "green";
    } else {
        result.textContent = `Invalid US number: ${phoneNumber}`;
        result.style.color = "red";
    }
}


const clearInput = () => {
    input.value = "";
    result.textContent = "";
}


Array.from(buttons).forEach(button => {
    button.addEventListener('click', handleButtonClick);
});

check.addEventListener("click", validatePhoneNumber);

clear.addEventListener("click", clearInput);


