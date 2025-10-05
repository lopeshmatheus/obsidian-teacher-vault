<%*
const fm = tp.frontmatter;
const aNota = tp.file.title;

// --- Início da Depuração ---
console.log(`--- Depurando a nota: ${aNota} ---`);
console.log("Propriedades encontradas pelo Templater:", fm);
// --- Fim da Depuração ---

const dataCompleta = fm.data;
const nomeDaNota = fm.nome;

if (dataCompleta && typeof dataCompleta === 'string' && nomeDaNota) {
    const [datePart, timePart] = dataCompleta.split(' ');

    if (timePart) {
        const startTime = timePart;
        const [hour, minute] = timePart.split(':');

        if (hour && minute) {
            const endTimeHour = parseInt(hour, 10) + 1;
            const endTime = `${endTimeHour.toString().padStart(2, '0')}:${minute}`;

            app.fileManager.processFrontMatter(tp.file.find_tfile(), (fm_update) => {
                fm_update.title = nomeDaNota;
                fm_update.date = datePart;
                fm_update.startTime = startTime;
                fm_update.endTime = endTime;
                delete fm_update.data;
                delete fm_update.nome;
            });

            new Notice(`Nota '${nomeDaNota}' atualizada!`, 4000);
        } else {
            new Notice(`Hora inválida na nota '${nomeDaNota}'. Pulando.`, 4000);
        }
    } else {
        new Notice(`Nota '${nomeDaNota}' não contém hora. Pulando.`, 4000);
    }
} else {
    // ESTA É A MENSAGEM DE ERRO MAIS IMPORTANTE
    new Notice(`ERRO: Propriedades 'data' ou 'nome' não foram encontradas na nota '${aNota}'. Verifique o console.`, 6000);
}

tR = "";
%>