<template>
    <div class="form-container" id="pdf-content">
        <h1>Zapisnik o Vršnju Tehničkog Pregleda</h1>

        <!-- Sekcija za osnovne informacije -->
        <div class="section">
            <label for="ime">Ime i prezime vlasnika:</label>
            <input type="text" id="ime" v-model="formData.ime" placeholder="Unesite ime i prezime">

            <label for="datum">Datum pregleda:</label>
            <input type="date" id="datum" v-model="formData.datum">
        </div>

        <!-- Sekcija za podatke o vozilu -->
        <div class="section">
            <label for="reg_broj">Registarski broj vozila:</label>
            <input type="text" id="reg_broj" v-model="formData.regBroj" placeholder="Unesite registarski broj">

            <label for="model">Model vozila:</label>
            <input type="text" id="model" v-model="formData.model" placeholder="Unesite model vozila">

            <label for="godina_proizvodnje">Godina proizvodnje:</label>
            <input type="number" id="godina_proizvodnje" v-model="formData.godinaProizvodnje"
                placeholder="Unesite godinu proizvodnje">
        </div>

        <!-- Sekcija za rezultate tehničkog pregleda -->
        <div class="section">
            <label for="rezultat">Rezultat pregleda:</label>
            <select id="rezultat" v-model="formData.rezultat">
                <option value="prošao">Prošao</option>
                <option value="nije prošao">Nije prošao</option>
            </select>
        </div>

        <!-- Dugme za generisanje PDF-a -->
        <button class="pdf-btn" @click="exportToPDF">Preuzmi kao PDF</button>
    </div>
</template>

<script>
import jsPDF from 'jspdf';
import html2canvas from 'html2canvas';

export default {
    data() {
        return {
            formData: {
                ime: '',
                datum: '',
                regBroj: '',
                model: '',
                godinaProizvodnje: '',
                rezultat: '',
            },
        };
    },
    methods: {
        exportToPDF() {
            // Sakrij dugme pre kreiranja PDF-a
            const pdfButton = document.querySelector('.pdf-btn');
            pdfButton.style.visibility = 'hidden';

            // Generisanje PDF-a
            const form = document.getElementById('pdf-content');
            html2canvas(form).then((canvas) => {
                const imgData = canvas.toDataURL('image/png');
                const doc = new jsPDF();
                doc.addImage(imgData, 'PNG', 10, 10);
                doc.save('tehnicki_pregled.pdf');

                // Ponovo prikaži dugme nakon kreiranja PDF-a
                pdfButton.style.visibility = 'visible';
            });
        },
    },
};
</script>

<style scoped>
.form-container {
    max-width: 600px;
    margin: auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
}

.section {
    margin-bottom: 15px;
}

label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
}

input,
select {
    width: 100%;
    padding: 8px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 3px;
}

button {
    padding: 10px 15px;
    background-color: #007bff;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background-color: #0056b3;
}

.pdf-btn {
    margin-left: 10px;
}
</style>
