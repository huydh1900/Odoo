# Odoo
- Plugin: XpathView + XSLT
- Alert:
  + window.alert("Patch Extended");
  + this.dialog.add(ConfirmationDialog
-
    @api.model
    def get_view(self, view_id=None, view_type='form', **options):
        res = super().get_view(view_id, view_type, **options)
        user = self.env.user
        if view_type == 'tree':
            doc = etree.XML(res['arch'])
            if user.has_group('boni_mrp.group_mrp_user_view_only') and not user.has_group('boni_mrp.group_mrp_user_the_reviewer'):
                for node in doc.xpath("//tree"):
                    node.set('export_xlsx', 'false')
                    self.print_node_details(node)
            res['arch'] = etree.tostring(doc)
        return res

    def print_node_details(self, node):
        print("Node Tag:", node.tag)
        print("Node Attributes:", node.attrib)
        for child in node:
            print("Child Tag:", child.tag)
            print("Child Attributes:", child.attrib)
# Git
git clone https://oauth2:ACESS_TOKEN@gitlab.hebela.vn/erp/bonita.git

