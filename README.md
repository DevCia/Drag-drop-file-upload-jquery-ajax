# Drag and drop file uploads with jQuery and AJAX


### jQuery
```JS
// Arrastar
$('.upload-content').on('dragenter', function (e) {

    e.stopPropagation();
    e.preventDefault();

    $(".upload-content-title").text("Solte aqui");

});

// Arrastar :hover
$('.upload-content').on('dragover', function (e) {

    e.stopPropagation();
    e.preventDefault();

    $(".upload-content-title").text("Solte aqui");

});

// Soltar
$('.upload-content').on('drop', function (e) {

    e.stopPropagation();
    e.preventDefault();

    $(".upload-content-title").text("Carregando...");

    var fd = new FormData();

    var file = e.originalEvent.dataTransfer.files;

    fd.append('file', file[0]);

    upload(fd);

});

// Abrir arquivo seletor quando clicar na div
$("#uploadfile").on('click', function () {
    $("#file").click();
});

// Arquivo selecionado
$("#file").change(function () {

    var fd = new FormData();

    var files = $('#file')[0].files[0];

    fd.append('file', files);

    upload(fd);

});

function upload(formData) {

    $.ajax({
        url: "upload.php",
        type: "POST",
        data: formData,
        contentType: false,
        processData: false,
        dataType: 'json',
        success: response => {

            console.log(response);

            $(".upload-content-title").text("Solte o arquivo aqui ou clique para selecionar o mesmo");

        }
    });

}

```
