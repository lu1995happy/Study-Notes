# Apple OA - type-ahead search widget

```markup
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Tianlin Lu's Interview Exercise</title>
  <style>
    * {
      box-sizing: border-box;
    }

    body {
      font: 15px Arial;
    }

    .search {
      position: relative;
      display: inline-block;
      width: 300px;
    }

    input {
      background-image: url(https://image.flaticon.com/icons/png/512/55/55369.png);
      background-position: 10px 10px;
      background-repeat: no-repeat;
      background-size: 20px;
      border: 1px solid transparent;
      background-color: whitesmoke;
      padding: 10px 20px 10px 40px; 
      font-size: 15px;
    }

    input[type=text] {
      background-color: whitesmoke;
      width: 100%;
    }

    #clear {
      position: absolute;
      right: 5px;
      top: 0;
      bottom: 0;
      height: 20px;
      margin: auto;
      font-size: 20px;
      cursor: pointer;
    }

    .items {
      position: absolute;
      border: 1px sold lightgrey;
      border-bottom: none;
      border-top: none;
      z-index: 99;
      top: 100%;
      left: 0;
      right: 0;
      overflow: auto;
      max-height: 200px;
    }

    [name=focus] {
      color: red;
    }

    .items div {
      padding: 10px;
      cursor: pointer;
      background-color: white;
      border-bottom: 1px solid lightgrey;
      height: 40px;
    }

    .items div:hover {
      background-color: #e9e9e9;
    }

    .active {
      background-color: blue !important;
      color: white;
    }
  </style>
  <script>
    // the searchWidget function takes two arguments, the input text field element 
    // and the array of possible values
    const searchWidget = (input, arr) => {
      // store the current focus position in the item list
      let currentFocus = 0;
      // set the default focused element to the input tag
      let focused = "input"; 
      // store all the tag IDs
      const navigateList = ["input", "clear", "inputlist"];
      const clearButton = document.getElementById("clear");
      const inputTag = document.getElementById("input");
      // execute the function when the input field value has changed
      input.addEventListener("input", function(e) {
        let value = this.value;
        closeAllLists();
        if (!value) {
          clearButton.innerHTML = "";
          return false;
        } else {
          // if the input field value is not empty, make the reset button active
          clearButton.innerHTML = "X";
        }
        currentFocus = -1;
        // create a DIV element that will contain all the items
        let list = document.createElement("DIV");
        list.setAttribute("id", this.id + "list");
        list.setAttribute("class", "items");
        // append the DIV element to the container
        this.parentNode.appendChild(list);
        for (let i = 0; i < arr.length; i++) {
          // check if input field value is the substring of the item
          if (arr[i].toUpperCase().includes(value.toUpperCase())) {
            // create the DIV element for each matching element
            let word = document.createElement("DIV");
            // using the Regular Expression to make the matched part bold
            const match = new RegExp(value, "gi");
            word.innerHTML = arr[i].replace(match, "<strong>" + value + "</strong>");
            // change the input field value to the item value if the item is clicked
            word.addEventListener("click", function(e) {
              input.value = this.innerText;
              closeAllLists();
            });
            list.appendChild(word);
          }
        }
      });
      // execute the function when the specific key is pressed
      input.addEventListener("keydown", function(e) {
        let item = document.getElementById(this.id + "list");
        if (item) {
          item = item.getElementsByTagName("div");
        }
        if (e.keyCode === 40) {
          // if the arrow DOWN key is pressed, increase the current focus variable,
          // and highlight the current item 
          currentFocus++;
          addActive(item);
          document.getElementsByTagName("div")[currentFocus].scrollIntoView();
        } else if (e.keyCode === 38) {
          // if the arrow UP key is pressed, increase the current focus variable, 
          // and highlight the current item
          currentFocus--;
          addActive(item);
          document.getElementsByTagName("div")[currentFocus].scrollIntoView();
        } else if (e.keyCode === 13) {
          // if the ENTER key is pressed, prevent the form from being submitted, clear the 
          // input field value and set focus on the input field tag
          e.preventDefault();
          clearButton.innerHTML = "";
          inputTag.value = ""; 
          closeAllLists();
          inputTag.focus();
        } else if (e.keyCode === 27) {
          // the ESC key part is not working correctly, since the active element is always 
          // the input tag, therefore, whenever ESC key is pressed, the input field value will be cleared
          e.preventDefault();
          if (document.activeElement === inputTag) {
            clearButton.innerHTML = "";
            inputTag.value = ""; 
            closeAllLists();
          } else {
            inputTag.focus();
          }
        } else if (e.keyCode === 9) {
          // if the TAB key is pressed, it will navigate between the input field, 
          // reset button and drop down menu
          e.preventDefault();
          navigate();
        }
      });

      // the function that add the active class to the target item 
      const addActive = (item) => {
        if (!item) {
          return false;
        }
        removeActive(item);
        if (currentFocus >= item.length) {
          currentFocus = 0;
        }
        if (currentFocus < 0) {
          currentFocus = item.length - 1;
        }
        item[currentFocus].classList.add("active");
      };

      // the function that remove the active class from all the items
      const removeActive = (item) => {
        for (let i = 0; i < item.length; i++) {
          item[i].classList.remove("active");
        }
      };

      // the function that close all the list in the document 
      const closeAllLists = (ele) => {
        let item = document.getElementsByClassName("items");
        for (let i = 0; i < item.length; i++) {
          if (ele !== item[i] && ele !== input) {
            item[i].parentNode.removeChild(item[i]);
          }
        }
        for (let i = 0; i < navigateList.length - 1; i++) {
          document.getElementById(navigateList[i]).removeAttribute("name", "focus");
        }
      };

      // the function that perform the navigate function for the TAB keys
      const navigate = () => {
        if (clearButton.innerHTML && document.getElementById("inputlist")) {
          let index = navigateList.indexOf(focused);
          document.getElementById(focused).removeAttribute("name", "focus");
          // document.getElementById(focused).blur();
          if (index === navigateList.length - 1) {
            index = 0;
          } else {
            index++;
          }
          focused = navigateList[index];
          document.getElementById(focused).setAttribute("name", "focus"); 
          document.getElementById(focused).focus();
        }
      }

      // document.getElementsByTagName("form")[0].addEventListener("focus", function(e) {
      //   event.target.style.background = "red";
      // }, true);

      // document.getElementsByTagName("form")[0].addEventListener("blur", function(e) {
      //   event.target.style.background = "";
      // }, true);
      
      // close all the list when clicking outside the input field tag
      document.addEventListener("click", function(e) {
        closeAllLists(e.target);
      });

      // add functionality to the reset button in order to clear the input field value
      clearButton.addEventListener("click", function(e) {
        clearButton.innerHTML = "";
        inputTag.value = ""; 
        inputTag.focus();
      })
    }
  </script>
</head>
<body>
  <form autocomplete="off">
    <div class="search">
      <input id="input" type="text" name="country" placeholder="Please start your search...">
      <span id="clear" class="button"></span> 
    </div>
  </form>
  <script>
    const countries = ["Afghanistan","Albania","Algeria","Andorra","Angola","Anguilla","Antigua &amp; Barbuda","Argentina","Armenia","Aruba","Australia","Austria","Azerbaijan","Bahamas","Bahrain","Bangladesh","Barbados","Belarus","Belgium","Belize","Benin","Bermuda","Bhutan","Bolivia","Bosnia &amp; Herzegovina","Botswana","Brazil","British Virgin Islands","Brunei","Bulgaria","Burkina Faso","Burundi","Cambodia","Cameroon","Canada","Cape Verde","Cayman Islands","Central Arfrican Republic","Chad","Chile","China","Colombia","Congo","Cook Islands","Costa Rica","Cote D Ivoire","Croatia","Cuba","Curacao","Cyprus","Czech Republic","Denmark","Djibouti","Dominica","Dominican Republic","Ecuador","Egypt","El Salvador","Equatorial Guinea","Eritrea","Estonia","Ethiopia","Falkland Islands","Faroe Islands","Fiji","Finland","France","French Polynesia","French West Indies","Gabon","Gambia","Georgia","Germany","Ghana","Gibraltar","Greece","Greenland","Grenada","Guam","Guatemala","Guernsey","Guinea","Guinea Bissau","Guyana","Haiti","Honduras","Hong Kong","Hungary","Iceland","India","Indonesia","Iran","Iraq","Ireland","Isle of Man","Israel","Italy","Jamaica","Japan","Jersey","Jordan","Kazakhstan","Kenya","Kiribati","Kosovo","Kuwait","Kyrgyzstan","Laos","Latvia","Lebanon","Lesotho","Liberia","Libya","Liechtenstein","Lithuania","Luxembourg","Macau","Macedonia","Madagascar","Malawi","Malaysia","Maldives","Mali","Malta","Marshall Islands","Mauritania","Mauritius","Mexico","Micronesia","Moldova","Monaco","Mongolia","Montenegro","Montserrat","Morocco","Mozambique","Myanmar","Namibia","Nauro","Nepal","Netherlands","Netherlands Antilles","New Caledonia","New Zealand","Nicaragua","Niger","Nigeria","North Korea","Norway","Oman","Pakistan","Palau","Palestine","Panama","Papua New Guinea","Paraguay","Peru","Philippines","Poland","Portugal","Puerto Rico","Qatar","Reunion","Romania","Russia","Rwanda","Saint Pierre &amp; Miquelon","Samoa","San Marino","Sao Tome and Principe","Saudi Arabia","Senegal","Serbia","Seychelles","Sierra Leone","Singapore","Slovakia","Slovenia","Solomon Islands","Somalia","South Africa","South Korea","South Sudan","Spain","Sri Lanka","St Kitts &amp; Nevis","St Lucia","St Vincent","Sudan","Suriname","Swaziland","Sweden","Switzerland","Syria","Taiwan","Tajikistan","Tanzania","Thailand","Timor L'Este","Togo","Tonga","Trinidad &amp; Tobago","Tunisia","Turkey","Turkmenistan","Turks &amp; Caicos","Tuvalu","Uganda","Ukraine","United Arab Emirates","United Kingdom","United States of America","Uruguay","Uzbekistan","Vanuatu","Vatican City","Venezuela","Vietnam","Virgin Islands (US)","Yemen","Zambia","Zimbabwe"];
    searchWidget(document.getElementById("input"), countries);
  </script>
</body>
</html>
```

